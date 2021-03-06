WDIO Mochawesome Reporter
=========================

![Build Status](https://travis-ci.org/fijijavis/wdio-mochawesome-reporter.svg?branch=master) [![NPM version](https://badge.fury.io/js/wdio-mochawesome-reporter.svg)](http://badge.fury.io/js/wdio-mochawesome-reporter) [![npm](https://img.shields.io/npm/dm/wdio-mochawesome-reporter.svg?maxAge=2592000)]() 

Generates test results in the json formated needed to create [Mochawesome](https://github.com/adamgruber/mochawesome) reports.


## Installation

```shell
npm install --save wdio-mochawesome-reporter
```

A dependency will be added to your `package.json`

```json
{
  "dependencies": {
    "wdio-mochawesome-reporter": "^1.0.0"
  }
}
```

## Using

 Add ```mochawesome``` to the reporters array in your wdio config file.

```js
// sample wdio.conf.js
module.exports = {
  // ...
  reporters: ['dot', 'mochawesome'],
  // ...
};
```

## Reporter Configurations

The following configuration options are supported:

|option|default|description|
|---|---|---|
|includeScreenshots|false|All screenshots captured during test execution will be embedded in the report|
|screenshotUseRelativePath|false|By default sreenshots embeded in a report use an absolute path.  Set this option to true and have screenshot paths be relative to the mochawesome report folder.  This is useful if you want to publish the report to a static web server or zip it as a complete artifact of a build|


To use a configuration option add a ```mochawesomeOpts``` section to your wdio config.  Then add any options.
```js
// sample wdio.conf.js
module.exports = {
  // ...
  reporters: ['dot', 'mochawesome'],
  mochawesomeOpts: {
      includeScreenshots:true,
      screenshotUseRelativePath:true
  },
  // ...
};
```



## Mochawesome Report Generator
To convert the json generated by this package into a Mochawesome report you will need to use the [Mochawesome Report Generator](https://github.com/adamgruber/mochawesome-report-generator).

In summary...

* Add the package to your project
```shell
npm install --save mochawesome-report-generator
```

* Add a script to your package.json to generate the report
```json
  "scripts": {
    "generateMochawesome":"marge path/to/results.json --reportTitle 'My Project Results'"
  },
```
1) `path/to/results.json` = path and name of json file
2) `--reportTitle 'My Project Results' = unique report title

## Version Compatibility
v1.x of ```wdio-mochawesome-reporter``` is compatible with ```2.3.2``` of ```mochawesome-report-generator```

v2.x of ```wdio-mochawesome-reporter``` is compatible with version ```3.1.3``` of ```mochawesome-report-generator```