# OFMT

This repository contain code formatter for Ottofeller projects.

## Install

```shell
npm install @ottofeller/ofmt --save-dev
```

## Configs

The project contains the following formatting configs:
- `.prettierrc` with basic code formatting rules
- `eslint.quality.cjs` with JS/TS-specific code style and quality rules
- `eslint.tailwind.cjs` with CSS-specific code style and quality rules

Direct use of configs is meant only for IDE support. For CLI runs use the provided executables.

## Executables

There are two _bin_ files that perform the code checking:
- `ofmt` - installer/prettier formatter
- `olint` - eslint formatter

### ofmt

#### Options:
- `-l` - a flag to perform checking only. Without the flag prettier will rewrite files with fixed formatting.
- _non-flag_ - the prettier target files. This can contain any of file paths, directory paths, and glob patterns.
- `install` - a non-flag argument that creates a symlink to prettier config file and adds/extends eslint config within _package.json_. The second argument is the destination path.\
NOTE: the `install` script does not attempt to overwrite existing `prettier` config - if a _.prettierrc_ file exists it is left as is. An existing `eslint` config is extended with _eslint.quality.cjs_.

#### Examples:

Check TS files with prettier
```bash
npx ofmt -l './src/**/*.ts'
```

Fix TS files with prettier
```bash
npx ofmt './src/**/*.ts'
```

Install _prettier_ and _eslint_ configs to your project
```bash
npx ofmt install .
```
NOTE: if run as _npm-script_ the path will be inferred:
```json
"scripts": {
  "ofmt:install": "ofmt install",
  ...
}
```
```bash
npm run ofmt:install
```

### olint

#### Options:
- _non-flag_ - the lint target files. This can contain any of file paths, directory paths, and glob patterns.

#### Examples:
```bash
npx olint './src/**/*.ts'
```