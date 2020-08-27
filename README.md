# Easy start with ESLint, Prettier, and TypeScript

These are the common settings for ESLint and Prettier to support JavaScript, React, and TypeScript.

## Installation

You can install this lint rules globally. However, installing per project is recommended so your projects have the same settings within team members and machines.

1. If you don't already have a `package.json` file, create one with `npm init -y`.
2. Then we need to install this:

```
npx install-peerdeps --dev eslint-config-sungl
```

3. Check your `package.json` to see the list of `devDependencies`.
4. Create a `.eslintrc` file in the root of your project's directory. And add this:

```
{
    "extends": [
        "sungl"
    ]
}
```

5. (The steps after this are optional and not recommended. Let your editor do the work!) You can add two scripts to your `package.json` to lint and/or fix:

```
"scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
},
```

6. Now you can manullay lint your code by running `npm run lint` and fix issues with `npm run lint:fix`.

## Your Own Settings

If you'd like to overwrite eslint or prettier settngs, you can add rules in your `.eslintrc` file.
[ESLint rules](https://eslint.org/docs/rules/) go directly under `"rules"`, and [Prettier options](https://prettier.io/docs/en/options.html) go under `"prettier/prettier"`.

```
{
  "extends": [
    "sungl"
  ],
  "rules": {
    "no-console": 2,
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "es5",
        "singleQuote": true,
        "printWidth": 120,
        "tabWidth": 8,
      }
    ]
  }
}
```

## VS Code Settings

Once you've done all your installation and settings above, you can make VS Code to lint and fix for your.

1. Install the [ESLint package](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint).
2. Open VS Code Preferences and edit `settings.json`.

```
"editor.formatOnSave": true,
"tslint.enable": false,
"eslint.enable": true,
"eslint.run": "onType",
"eslint.format.enable": true,
// turn it off for JS and JSX, we will do this via eslint
"[javascript]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
},
"[javascriptreact]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
},
"[typescript]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
},
"[typescriptreact]": {
    "editor.defaultFormatter": "dbaeumer.vscode-eslint"
},
// tell the ESLint plugin to run on save
"editor.codeActionsOnSave": {
    "source.fixAll": true
},
// Optional BUT IMPORTANT: If you have the prettier extension enabled for other languages like CSS and HTML, turn it off for JS since we are doing it through Eslint already
"prettier.disableLanguages": ["javascript", "javascriptreact", "typescript", "typescriptreact"],
```
