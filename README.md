[![Codacy Badge](https://api.codacy.com/project/badge/Grade/4ffd0a188386439cb80e9b25adf1252f)](https://www.codacy.com/app/se-panfilov/strip-code-loader?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=se-panfilov/strip-code-loader&amp;utm_campaign=Badge_Grade)
[![](https://api.codeclimate.com/v1/badges/9a43a0ab347c227334fa/maintainability)](https://codeclimate.com/github/se-panfilov/strip-code-loader/maintainability)
[![Build Status](https://travis-ci.org/se-panfilov/strip-code-loader.svg?branch=master)](https://travis-ci.org/se-panfilov/strip-code-loader)
[![GitHub license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/se-panfilov/strip-code-loader/blob/master/LICENSE)


[![NPM](https://nodei.co/npm/strip-code-loader.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/vue-notifications/)
[![JavaScript Style Guide](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)


--------------------------
UNDER CONSTRUCTION
--------------------------

# strip-code-loader

A webkit loader to remove parts of code based on regular expressions.

Can be used to remove sections of code.

### Why? And what it does?

_Why_: For example you may want to remove code from production builds, but keep it in development and test environments.

Usefull to remove code from production builds that are only needed in development and test environments, or to remove custom internationalized information.
_What it does_: This plugin uses start and end comments to identify the code sections to strip out. For example:


```js
/*START.TESTS_ONLY*/
VueNotifications._private = {} //'_private' object would be exist only during the test time
VueNotifications._private.getVersion = getVersion // And I would be able to test 'getVersion' function (otherwise it won't be accesible because of the closure
/*END.TESTS_ONLY*/
```
(example from [vue-notifications](https://github.com/se-panfilov/vue-notifications) library)

or a bit simpler:

```js
/* test-code */
removeMeInProduction();
/* end-test-code */

doNotRemoveMe();
```

**Attention**: You have to use `/* ... */` for such comments, not just `// ...`

## Getting Started
First, install `strip-code-loader` as a development dependency:

```shell
npm i strip-code-loader --save-dev
#or
yarn add strip-code-loader --dev
```

## Example config

TODOTODOTODO
TODOTODOTODO
TODOTODOTODO
TODOTODOTODO

WOAH-WOAH, what if I want to **remove the comments conditionnaly**?

You may use [strip-code-loader](https://github.com/AgronKabashi/strip-code-loader) plugin for that case, for instance:

```js
const isProduction = process.env.buildTarget === "production" //assuming you'd run it with something like "cross-env BABEL_ENV=production && rollup -c"
...
plugins: [
  conditional(isProduction, [
    stripCode({
      start_comment: 'START.TESTS_ONLY',
      end_comment: 'END.TESTS_ONLY'
    })
  ])
]
...
```

### Options

#### options.start_comment
Type: `String`
Default value: `start_comment`

The text inside the opening comment used to identify code to strip.

#### options.end_comment
Type: `String`
Default value: `end_comment`

The text inside the closing comment used to identify code to strip.

#### options.pattern
Type: `RegExp`
Default value: (a generated RegExp matching the start and end comments)

If the default start and end comment matching doesn't work for you needs, you can supply your own RegExp to match against. If the `pattern` option is specified, the `start_comment` and `end_comment` options are ignored.

## Tests

```shell
npm test
```

## Same plugins for another tools

 - Rollup [rollup-plugin-strip-code](https://github.com/se-panfilov/rollup-plugin-strip-code)
 - Grunt [grunt-strip-code](https://github.com/nuzzio/grunt-strip-code)
 - Gulp [gulp-strip-code](https://github.com/massick/gulp-strip-code)

## Contributing
Feel free and go ahead.

## License

MIT License

Copyright (c) 2017 Sergei Panfilov

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
