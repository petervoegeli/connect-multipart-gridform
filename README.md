#connect-multipart-gridform
============================

[Connect](https://github.com/senchalabs/connect) compatible multipart middleware configured to stream uploads directly to MongoDB GridFS.

## install

```
npm install connect-multipart-gridform
```

## use

```js
var multipart = require('connect-multipart-gridform');
app.use(multipart(options));
```

## options

Options work the same way as in the connect [multipart](http://www.senchalabs.org/connect/multipart.html) middleware, with these additions:

  - db: (required) an open [node-mongodb-native](https://github.com/mongodb/node-mongodb-native) db instance
  - mongo: (required) the [node-mongodb-native](https://github.com/mongodb/node-mongodb-native) driver you created the db with
  - filename: (optional) function

The optional `filename` function is passed the `file.name` before streaming to MongoDB providing an opportunity to customize the filename with a prefix etc.

_For the curious, the options are first passed into a [gridform](https://github.com/aheckmann/gridform) before passing on to connects multiple middleware._

## why?

Connect multipart middleware uses [formidable](https://github.com/felixge/node-formidable) to process file uploads. `formidable` streams the files to disk. Now you can stream directly into GridFS.

## dependencies

`connect-multipart-gridform` utilizes both the [gridform](https://github.com/aheckmann/gridform) and [connect multipart](http://www.senchalabs.org/connect/multipart.html) modules which are directly exposed as:

    var multipart = require('connect-multipart-gridform');
    var gridform = multipart.gridform;
    var connectMultipart = multipart.multipart;

## tests

Run the tests with `make test`.

## express

Currently only works with Express 3.

## example

[https://github.com/aheckmann/connect-multipart-gridform/tree/master/examples](https://github.com/aheckmann/connect-multipart-gridform/tree/master/examples)

[LICENSE](https://github.com/aheckmann/connect-multipart-gridform/blob/master/LICENSE)

