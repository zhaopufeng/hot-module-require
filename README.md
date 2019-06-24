# hot-module-require

<!--[![build status](https://img.shields.io/travis/imcuttle/hot-module-require/master.svg?style=flat-square)](https://travis-ci.org/imcuttle/hot-module-require)-->

<!--[![Test coverage](https://img.shields.io/codecov/c/github/imcuttle/hot-module-require.svg?style=flat-square)](https://codecov.io/github/imcuttle/hot-module-require?branch=master)-->

[![NPM version](https://img.shields.io/npm/v/hot-module-require.svg?style=flat-square)](https://www.npmjs.com/package/hot-module-require)
[![NPM Downloads](https://img.shields.io/npm/dm/hot-module-require.svg?style=flat-square&maxAge=43200)](https://www.npmjs.com/package/hot-module-require)

Detect module's update recursively on nodejs.

## Usage

```javascript
// module.js
module.exports = require('./foo') + require('./bar')
```

```javascript
const makeHotRequire = require('hot-module-require')
const hotRequire = makeHotRequire(__dirname)

let mExports = require('./module')

hotRequire.accept(['./module'], (oldModule, path) => {
  // Do something here 
  // when './module' module or submodules('./foo', './bar'') be detected changed.
  let newExports = require('./module') 
})


// Or use it like follows
const hotModuleGetter = hotRequire('./module')
hotModuleGetter() // Returns the already updated `require('./module')``

hotModuleGetter.remove() // Calls `remove` for interrupting detect updated 
```

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### makeHotRequireFunction

[index.js:52-372](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L52-L372 "Source code on GitHub")

-   **See: More options see [detect-dep](https://github.com/imcuttle/detect-dep)**

make a hot require instance

#### Parameters

-   `dirname`   (optional, default `''`)
-   `presetOpts`  {{}} (optional, default `{}`)
    -   `presetOpts.recursive`  {boolean} Analysis file recursively (optional, default `true`)

Returns **[HotRequire](#hotrequire)** 

### HotRequire

[index.js:172-185](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L172-L185 "Source code on GitHub")

### resolve

[index.js:255-255](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L255-L255 "Source code on GitHub")

Resolve file name

#### Parameters

-   `name`  {string}

### watcher

[index.js:262-262](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L262-L262 "Source code on GitHub")

-   **See: [chokidar](https://npmjs.com/chokidar)**

file Watcher

### emitter

[index.js:268-268](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L268-L268 "Source code on GitHub")

The event emitter

### dependent

[index.js:275-275](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L275-L275 "Source code on GitHub")

The map about dependent relations

Type: [Map](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Map)

### dependence

[index.js:282-282](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L282-L282 "Source code on GitHub")

The map about dependence relations

Type: [Map](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Map)

### getDependenceTree

[index.js:292-292](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L292-L292 "Source code on GitHub")

-   **See: <https://github.com/imcuttle/detect-dep#tree>**

Get dependence tree of which file

#### Parameters

-   `modulePath`  {string}
-   `opts`  

Returns **{}** 

### addDependencies

[index.js:302-302](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L302-L302 "Source code on GitHub")

Add Dependencies

#### Parameters

-   `modulePath`  {string}
-   `deps`  {string\[]}

### removeDependencies

[index.js:310-310](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L310-L310 "Source code on GitHub")

Remove Dependencies

#### Parameters

-   `modulePath`  {string}
-   `deps`  {string\[]}

### accept

[index.js:319-330](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L319-L330 "Source code on GitHub")

Watch file with callback and make dependence(dependent) relations

#### Parameters

-   `deps`  {string\[]}
-   `callback`  {function}

### refuse

[index.js:338-360](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L338-L360 "Source code on GitHub")

Watch file with callback and make dependence(dependent) relations

#### Parameters

-   `deps`  {string\[]}
-   `callback`  {function}

### close

[index.js:367-369](https://github.com/imcuttle/hot-module-require/blob/af7414770828a349a80926db3ba9d11325bd4a15/index.js#L367-L369 "Source code on GitHub")

Close file watcher

Returns **any** void

## Related

-   [detect-dep](https://github.com/imcuttle/detect-dep) - Detect file's dependencies.
