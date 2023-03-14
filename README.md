# ext-build-action
GitHub action to build external dependencies

## Usage

### To use the action

```yaml
steps:
- uses: tst-race/ext-build-action@v1
  with:
    target: linux-arm64-v8a
```

#### inputs

The following inputs can be used as `step.with` keys

| Name         | Type   | Description
|--------------|--------|------------
| `target`     | String | Target platform and architecture (e.g., `linux-x86_64`, `android-arm64-v8a`)
| `path`       | String | Path to project build context (default is `.`)
| `cache`      | String | Name of build cache directory (default is `ext-cache`)
| `repository` | String | ext-builder repository (default is `tst-race/ext-builder`)
| `ref`        | String | ext-builder tag/ref (default is `v1`)

### To use the reusable workflow

```yaml
on:
  push:

permissions:
  contents: write

jobs:
  build:
    uses: tst-race/ext-build-action/.github/workflows/build-ext.yml@v1
```

#### inputs

The following inputs can be used as `jobs.<id>.with` keys

| Name                     | Type    | Description
|--------------------------|---------|------------
| `skip-linux-x86_64`      | Boolean | Skip building for Linux x86_64 (default is `false`)
| `skip-linux-arm64-v8a`   | Boolean | Skip building for Linux arm64-v8a (default is `false`)
| `skip-android-x86_64`    | Boolean | Skip building for Android x86_64 (default is `false`)
| `skip-android-arm64-v8a` | Boolean | Skip building for Android arm64-v8a (default is `false`)
