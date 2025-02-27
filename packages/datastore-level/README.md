# datastore-level <!-- omit in toc -->

[![ipfs.tech](https://img.shields.io/badge/project-IPFS-blue.svg?style=flat-square)](https://ipfs.tech)
[![Discuss](https://img.shields.io/discourse/https/discuss.ipfs.tech/posts.svg?style=flat-square)](https://discuss.ipfs.tech)
[![codecov](https://img.shields.io/codecov/c/github/ipfs/js-stores.svg?style=flat-square)](https://codecov.io/gh/ipfs/js-stores)
[![CI](https://img.shields.io/github/actions/workflow/status/ipfs/js-stores/js-test-and-release.yml?branch=main\&style=flat-square)](https://github.com/ipfs/js-stores/actions/workflows/js-test-and-release.yml?query=branch%3Amain)

> Datastore implementation with level(up|down) backend

## Table of contents <!-- omit in toc -->

- [Install](#install)
  - [Browser `<script>` tag](#browser-script-tag)
- [Usage](#usage)
  - [Browser Shimming Leveldown](#browser-shimming-leveldown)
  - [Database names](#database-names)
- [API Docs](#api-docs)
- [License](#license)
- [Contribute](#contribute)

## Install

```console
$ npm i datastore-level
```

### Browser `<script>` tag

Loading this module through a script tag will make it's exports available as `DatastoreLevel` in the global namespace.

```html
<script src="https://unpkg.com/datastore-level/dist/index.min.js"></script>
```

## Usage

```js
import { LevelDatastore } from 'datastore-level'

// Default using level as backend for node or the browser
const store = new LevelDatastore('path/to/store')

// another leveldown compliant backend like memory-level
const memStore = new LevelDatastore(
  new MemoryLevel({
    keyEncoding: 'utf8',
    valueEncoding: 'view'
  })
)
```

### Browser Shimming Leveldown

`LevelStore` uses the `level` module to automatically use `level` if a modern bundler is used which can detect bundle targets based on the `pkg.browser` property in your `package.json`.

If you are using a bundler that does not support `pkg.browser`, you will need to handle the shimming yourself, as was the case with versions of `LevelStore` 0.7.0 and earlier.

### Database names

`level-js@3` changed the database prefix from `IDBWrapper-` to `level-js-`, so please specify the old prefix if you wish to continue using databases created using `datastore-level` prior to `v0.12.0`.  E.g.

```javascript
import leveljs from 'level-js'
import browserStore = new LevelDatastore(
  new Level('my/db/name', {
    prefix: 'IDBWrapper-'
  })
})
```

More information: [https://github.com/Level/level-js/blob/master/UPGRADING.md#new-database-prefix](https://github.com/Level/level-js/blob/99831913e905d19e5f6dee56d512b7264fbed7bd/UPGRADING.md#new-database-prefix)

## API Docs

- <https://ipfs.github.io/js-stores/modules/datastore_level.html>

## License

Licensed under either of

- Apache 2.0, ([LICENSE-APACHE](LICENSE-APACHE) / <http://www.apache.org/licenses/LICENSE-2.0>)
- MIT ([LICENSE-MIT](LICENSE-MIT) / <http://opensource.org/licenses/MIT>)

## Contribute

Contributions welcome! Please check out [the issues](https://github.com/ipfs/js-stores/issues).

Also see our [contributing document](https://github.com/ipfs/community/blob/master/CONTRIBUTING_JS.md) for more information on how we work, and about contributing in general.

Please be aware that all interactions related to this repo are subject to the IPFS [Code of Conduct](https://github.com/ipfs/community/blob/master/code-of-conduct.md).

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.

[![](https://cdn.rawgit.com/jbenet/contribute-ipfs-gif/master/img/contribute.gif)](https://github.com/ipfs/community/blob/master/CONTRIBUTING.md)
