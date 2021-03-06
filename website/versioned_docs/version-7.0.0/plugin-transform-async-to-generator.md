---
id: version-7.0.0-babel-plugin-transform-async-to-generator
title: @babel/plugin-transform-async-to-generator
sidebar_label: transform-async-to-generator
original_id: babel-plugin-transform-async-to-generator
---

> In Babel 7, `transform-async-to-module-method` was merged into this plugin

## Example

**In**

```javascript
async function foo() {
  await bar();
}
```

**Out**

```javascript
var _asyncToGenerator = function (fn) {
  ...
};
var foo = _asyncToGenerator(function* () {
  yield bar();
});
```

**Out with options**

> Turn async functions into a Bluebird coroutine

```javascript
var Bluebird = require("bluebird");

var foo = Bluebird.coroutine(function* () {
  yield bar();
});
```

## Installation

```sh
npm install --save-dev @babel/plugin-transform-async-to-generator
```

## Usage

### With a configuration file (Recommended)

Without options:

```json
{
  "plugins": ["@babel/plugin-transform-async-to-generator"]
}
```

With options:

```json
{
  "plugins": [
    ["@babel/plugin-transform-async-to-generator", {
      "module": "bluebird",
      "method": "coroutine"
    }]
  ]
}
```

### Via CLI

```sh
babel --plugins @babel/plugin-transform-async-to-generator script.js
```

### Via Node API

```javascript
require("@babel/core").transform("code", {
  plugins: ["@babel/plugin-transform-async-to-generator"]
});
```

## References

* [Proposal: Async Functions for ECMAScript](https://github.com/tc39/ecmascript-asyncawait)

