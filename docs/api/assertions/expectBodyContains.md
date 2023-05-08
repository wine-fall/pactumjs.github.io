---
tags:
  - body
  - assert body
  - assert text
---

# expectBodyContains

Performs partial equal on body text. 

> *Use this for text comparison.*

## Syntax

```js
expectBodyContains(body)
```

## Usage

### ✅  Correct Usage

```js 
await spec()
  .get('/api/health')
  .expectBodyContains('OK');
```

```js 
// bdd style
const _spec = await spec().get('/api/health');
_spec.response().to.have.bodyContains('OK');
```

## Arguments

#### > body (string)

Response body.

## Examples

Normal
```js
const { spec } = require('pactum');

await spec()
  .get('https://httpbin.org/robots.txt')
  .expectBodyContains(`User-agent: *`);
```

Work with `stores`
```js
const { spec } = require('pactum');

await spec()
  .get('http://jsonplaceholder.typicode.com/posts')
  .expectStatus(200)
  .stores('FirstPostId', '[0].id');

await spec()
  .get('https://httpbin.org/robots.txt')
  .expectBodyContains('$S{FirstPostId}');
```
