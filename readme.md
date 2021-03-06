The `kor-redis` library exported as ```NodeJS``` module.

[![NPM Version][npm-image]][npm-url]
[![NPM Downloads][downloads-image]][downloads-url]
[![Build Status][travis-image-url]][travis-url]
[![Greenkeeper badge](https://badges.greenkeeper.io/razaqK/kor-redis.svg)](https://greenkeeper.io/)

# Installation

This is a [Node.js](https://nodejs.org/en/) module available through the
[npm registry](https://www.npmjs.com/). Installation is done using the
[`npm install` command](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):
```
   $ npm i npm
   $ npm i --save kor-redis
```

:rotating_light:
### New Features
- Generic command function to run any redis command

#### Features
- Get remaining expiration time if set on key
- Extend expiration time
- Remove expiration (persist the redis key)
- Rename redis key

### Usage: In NodeJS

```diff
+ Added command method that allow the use of all redis commands.

// Load pmodule
const Redis = require('kor-redis');
const redis = new Redis('host', 'port', 'db');

redis.command('set', ['key', 'value']);
```

See Redis Commands here [Redis.io](https://redis.io/commands)

```
// Load pmodule
const Redis = require('kor-redis');
const redis = new Redis('host', 'port', 'db');

// setting value. Note value can be an object, an array, string or number
redis.set(key, value)

// setting value and expiring time. Note value can be an object, an array, string or number
redis.set(key, value, 5) // this expires in 5s

// get value store in redis
redis.get(key).then(value => {
    console.log(value)
})

// get all keys in redis
redis.getKeys().then(keys => {
    console.log(keys)
})

// delete key in redis
redis.del(key)

// delete all keys in redis
redis.delAll()

// set new (if no expiration time) or increase the expiration time on a key 
redis.setExpiryTime(key, 5).then(res => {
    console.log(res)
})

// check the remain expiration on a key
redis.remainExpiryTimeInSeconds(key).then(res => {
    console.log(res)
})

// remove expiration from a key
redis.persist(key).then(res => {
    console.log(res)
})

// rename a redis key to new one
redis.renameKey(key, newKey).then(res => {
    console.log(res)
})
```

See the [package source](https://github.com/razaqK/kor-redis) for more detail.

[npm-image]: https://img.shields.io/npm/v/kor-redis.svg
[npm-url]: https://npmjs.org/package/kor-redis
[downloads-image]: https://img.shields.io/npm/dm/kor-redis.svg
[downloads-url]: https://npmjs.org/package/kor-redis
[travis-url]: https://travis-ci.org/razaqK/kor-redis
[travis-image-url]: https://travis-ci.org/razaqK/kor-redis.svg?branch=master
