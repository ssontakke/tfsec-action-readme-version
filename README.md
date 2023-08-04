<p align="center">
  <img width="354" src="./tfsec.png">
</p>

# tfsec-action
Run tfsec as a GitHub action with configurable output

To add the action, add `tfsec.yml` into the `.github/workflows` directory in the root of your Github project.

The contents of `tfsec.yml` should be;

```yaml
name: tfsec
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  tfsec:
    name: tfsec
    runs-on: ubuntu-latest

    steps:
      - name: Clone repo
        uses: actions/checkout@master
      - name: tfsec
        uses: aquasecurity/tfsec-action
```

Run tfsec as part of a GitHub Action flow. Optionally prevent the failure of tfsec from breaking the build or pass additional arguments using `additional_args`.

## Optional inputs

There are a number of optional inputs that can be used in the `with:` block.

**working_directory** - the directory to scan in, defaults to `.`, ie current working directory

**version** - the version of tfsec to use, defaults to `latest`

**format** - Default format can be overridden to any of the following - [json,csv,checkstyle,junit,sarif]

**additional_args** - any additional arguments you want to have passed to tfsec

**soft_fail** - set to `true` if you dont want the action to break the build

**github_token** - a GitHub token to be used when calling the GitHub API, which helps in avoiding rate-limiting

### tfsec_vars

`tfsec` provides an [extensive number of arguments](https://aquasecurity.github.io/tfsec/v0.63.1/getting-started/usage/) which can be passed through as in the example below;

```yaml
name: tfsec
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  tfsec:
    name: tfsec
    runs-on: ubuntu-latest

    steps:
      - name: Clone repo
        uses: actions/checkout@master
      - name: tfsec
        uses: aquasecurity/tfsec-action@v1.0.0
        with:
          soft_fail: true

```

## Open Source Attribution

- bash: [GPL 3.0 or later](https://www.gnu.org/licenses/gpl-3.0.html)
- curl: [curl license](https://curl.se/docs/copyright.html)
- git: [GPL 2.0 or later](https://github.com/git/git/blob/master/COPYING)
- jq: [MIT](https://github.com/stedolan/jq/blob/master/COPYING)

## License

[MIT License](https://github.com/nkuik/tfsec-action/blob/master/LICENSE)
