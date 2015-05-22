SuperAgent as Promise(d)
=====================

[SuperAgent](http://visionmedia.github.io/superagent/) as [Promise](https://github.com/petkaantonov/bluebird/blob/master/API.md)

This is a fork of shimore's `superagent-as-promised` library on GitHub. Due to a weird quirk of Supergent as described in [this issue](https://github.com/visionmedia/superagent/issues/225), we've added a `buffer` call before `end`, and moved it to GitHub. 

Installation
------------

    npm install https://github.com/studionone/superagent-as-promised.git

Usage
-----

    var request = require('superagent');
    require('superagent-as-promised')(request);

Then

    request
    .get('/location')
    .then( function(response) {
      console.log("Got "+response.text);
    })
    .catch( function(error) {
      console.dir(error);
    })

is syntactic sugar for:

    var promise = request
      .get('/location')
      .endAsync();

    promise
      .then( function(response) {
        console.log("Got "+response.text);
      })
      .catch( function(error) {
        console.dir(error);
      })
