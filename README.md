# pkgcloud-bootstrapper
`pkgcloud.core.Bootstrapper` extracted into its own module.

## Usage

```js
var pkgcloud = require('pkgcloud');
var Bootstrapper = require('pkgcloud-bootstrapper');

var client = pkgcloud.compute.createClient({
  // Provider options
});

var bootstrapper = new Bootstrapper({ compute: client });
var ee = bootstrapper.createServer({
  name: 'mad_torvald',
  image: 'ubuntu-13.10',
  flavor: '512mb'
});

ee.on('error', function (err) {
  // Handle error.
});

ee.on('create', function (server) {
  // We received a reply to our creation request from the provider.
});

ee.on('active', function (server) {
  // Server is now active (accepting SSH connections).
});

ee.on('complete', function (server) {
  // Server was bootstrapped and creation is complete
});
```
