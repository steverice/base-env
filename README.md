# base-env [![NPM version](https://img.shields.io/npm/v/base-env.svg)](https://www.npmjs.com/package/base-env) [![Build Status](https://img.shields.io/travis/jonschlinkert/base-env.svg)](https://travis-ci.org/jonschlinkert/base-env)

> Runner plugin for base-methods, for building up the user's environment object.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install base-env --save
```

## Usage

```js
var Base = require('base');
var env = require('base-env');
```

**Prototype plugin**

Register as a prototype plugin if you want the `.createEnv` method to be added to all instances of `base`:

```js
Base.use(env());
```

**Instance plugin**

Register as an instance plugin if you only want the `.createEnv` method to be added to a specific instance:

```js
var base = new Base();
base.use(env());
```

## API

Create an `env` object with the given `name`, function, filepath
or app instance, and options.

**Params**

* `name` **{String}**
* `val` **{Object|Function|String}**
* `options` **{Object}**
* `returns` **{Object}**

### [.env.isMatch](lib/app.js#L53)

Returns true if the given `str` matches `env.key`, `env.name` or `env.alias`. When env is created from a filepath, the following properties are also checked:

* `env.dirname`
* `env.path`
* `env.basename`

**Params**

* `str` **{String}**: The string to match
* `returns` **{Boolean}**: Retuns true if a match is made.

**Example**

```js
var env = app.createEnv('foo', function() {});
env.isMatch('bar');
//=> false
```

### [.env.invoke](lib/app.js#L76)

When `env` is created from an existing application instance, the instance is cached on `env.app` and `env.invoke` is a noop function that simply returns `env.app`.

* `returns` **{Object}**: Returns the invoked instance.

**Example**

```js
var foo = new Base();
var bar = new Base();

var env = foo.createEnv('bar', function() {});
env.invoke(bar);
//=> `env.fn` is invoked with `bar`
```

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/base-env/issues/new).

## Building docs

Generate readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install verb && npm run docs
```

Or, if [verb](https://github.com/verbose/verb) is installed globally:

```sh
$ verb
```

## Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

## Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2016 [Jon Schlinkert](https://github.com/jonschlinkert)
Released under the [MIT license](https://github.com/jonschlinkert/base-env/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on March 13, 2016._