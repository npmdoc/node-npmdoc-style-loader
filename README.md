# api documentation for  [style-loader (v0.16.1)](https://github.com/webpack/style-loader#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-style-loader.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-style-loader) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-style-loader.svg)](https://travis-ci.org/npmdoc/node-npmdoc-style-loader)
#### style loader module for webpack

[![NPM](https://nodei.co/npm/style-loader.png?downloads=true)](https://www.npmjs.com/package/style-loader)

[![apidoc](https://npmdoc.github.io/node-npmdoc-style-loader/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-style-loader_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-style-loader/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-style-loader/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-style-loader/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Tobias Koppers @sokra"
    },
    "bugs": {
        "url": "https://github.com/webpack/style-loader/issues"
    },
    "dependencies": {
        "loader-utils": "^1.0.2"
    },
    "description": "style loader module for webpack",
    "devDependencies": {
        "css-loader": "^0.27.3",
        "file-loader": "^0.10.1",
        "jsdom": "^9.11.0",
        "memory-fs": "^0.4.1",
        "mocha": "^3.2.0",
        "standard-version": "^4.0.0",
        "webpack": "^2.2.1"
    },
    "directories": {},
    "dist": {
        "shasum": "50e325258d4e78421dd9680636b41e8661595d10",
        "tarball": "https://registry.npmjs.org/style-loader/-/style-loader-0.16.1.tgz"
    },
    "gitHead": "5f56f9fd56aab7965d4eba28019d6e6079f5d610",
    "homepage": "https://github.com/webpack/style-loader#readme",
    "license": "MIT",
    "maintainers": [
        {
            "name": "bebraw",
            "email": "bebraw@gmail.com"
        },
        {
            "name": "d3viant0ne",
            "email": "wiens.joshua@gmail.com"
        },
        {
            "name": "ericclemmons",
            "email": "eric@smarterspam.com"
        },
        {
            "name": "jhnns",
            "email": "mail@johannesewald.de"
        },
        {
            "name": "sokra",
            "email": "tobias.koppers@googlemail.com"
        },
        {
            "name": "thelarkinn",
            "email": "sean.larkin@cuw.edu"
        }
    ],
    "name": "style-loader",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/webpack/style-loader.git"
    },
    "scripts": {
        "release": "yarn run standard-version",
        "test": "mocha",
        "travis:test": "yarn run test"
    },
    "version": "0.16.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module style-loader](#apidoc.module.style-loader)
1.  [function <span class="apidocSignatureSpan">style-loader.</span>pitch (remainingRequest)](#apidoc.element.style-loader.pitch)
1.  [function <span class="apidocSignatureSpan">style-loader.</span>url ()](#apidoc.element.style-loader.url)
1.  [function <span class="apidocSignatureSpan">style-loader.</span>useable ()](#apidoc.element.style-loader.useable)

#### [module style-loader.url](#apidoc.module.style-loader.url)
1.  [function <span class="apidocSignatureSpan">style-loader.</span>url ()](#apidoc.element.style-loader.url.url)
1.  [function <span class="apidocSignatureSpan">style-loader.url.</span>pitch (remainingRequest)](#apidoc.element.style-loader.url.pitch)

#### [module style-loader.useable](#apidoc.module.style-loader.useable)
1.  [function <span class="apidocSignatureSpan">style-loader.</span>useable ()](#apidoc.element.style-loader.useable.useable)
1.  [function <span class="apidocSignatureSpan">style-loader.useable.</span>pitch (remainingRequest)](#apidoc.element.style-loader.useable.pitch)



# <a name="apidoc.module.style-loader"></a>[module style-loader](#apidoc.module.style-loader)

#### <a name="apidoc.element.style-loader.pitch"></a>[function <span class="apidocSignatureSpan">style-loader.</span>pitch (remainingRequest)](#apidoc.element.style-loader.pitch)
- description and source-code
```javascript
pitch = function (remainingRequest) {
	if(this.cacheable) this.cacheable();
	var query = loaderUtils.getOptions(this) || {};
	return [
		"// style-loader: Adds some css to the DOM by adding a <style> tag",
		"",
		"// load the styles",
		"var content = require(" + loaderUtils.stringifyRequest(this, "!!" + remainingRequest) + ");",
		"if(typeof content === 'string') content = [[module.id, content, '']];",
		"// add the styles to the DOM",
		"var update = require(" + loaderUtils.stringifyRequest(this, "!" + path.join(__dirname, "addStyles.js")) + ")(content, " + JSON
.stringify(query) + ");",
		"if(content.locals) module.exports = content.locals;",
		"// Hot Module Replacement",
		"if(module.hot) {",
		"	// When the styles change, update the <style> tags",
		"	if(!content.locals) {",
		"		module.hot.accept(" + loaderUtils.stringifyRequest(this, "!!" + remainingRequest) + ", function() {",
		"			var newContent = require(" + loaderUtils.stringifyRequest(this, "!!" + remainingRequest) + ");",
		"			if(typeof newContent === 'string') newContent = [[module.id, newContent, '']];",
		"			update(newContent);",
		"		});",
		"	}",
		"	// When the module is disposed, remove the <style> tags",
		"	module.hot.dispose(function() { update(); });",
		"}"
	].join("\n");
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.style-loader.url"></a>[function <span class="apidocSignatureSpan">style-loader.</span>url ()](#apidoc.element.style-loader.url)
- description and source-code
```javascript
url = function () {}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.style-loader.useable"></a>[function <span class="apidocSignatureSpan">style-loader.</span>useable ()](#apidoc.element.style-loader.useable)
- description and source-code
```javascript
useable = function () {}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.style-loader.url"></a>[module style-loader.url](#apidoc.module.style-loader.url)

#### <a name="apidoc.element.style-loader.url.url"></a>[function <span class="apidocSignatureSpan">style-loader.</span>url ()](#apidoc.element.style-loader.url.url)
- description and source-code
```javascript
url = function () {}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.style-loader.url.pitch"></a>[function <span class="apidocSignatureSpan">style-loader.url.</span>pitch (remainingRequest)](#apidoc.element.style-loader.url.pitch)
- description and source-code
```javascript
pitch = function (remainingRequest) {
	this.cacheable && this.cacheable();
	var query = loaderUtils.getOptions(this) || {};
	return [
		"// style-loader: Adds some reference to a css file to the DOM by adding a <link> tag",
		"var update = require(" + JSON.stringify("!" + path.join(__dirname, "addStyleUrl.js")) + ")(",
		"\trequire(" + loaderUtils.stringifyRequest(this, "!!" + remainingRequest) + ")",
		", " + JSON.stringify(query) + ");",
		"// Hot Module Replacement",
		"if(module.hot) {",
		"\tmodule.hot.accept(" + loaderUtils.stringifyRequest(this, "!!" + remainingRequest) + ", function() {",
		"\t\tupdate(require(" + loaderUtils.stringifyRequest(this, "!!" + remainingRequest) + "));",
		"\t});",
		"\tmodule.hot.dispose(function() { update(); });",
		"}"
	].join("\n");
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.style-loader.useable"></a>[module style-loader.useable](#apidoc.module.style-loader.useable)

#### <a name="apidoc.element.style-loader.useable.useable"></a>[function <span class="apidocSignatureSpan">style-loader.</span>useable ()](#apidoc.element.style-loader.useable.useable)
- description and source-code
```javascript
useable = function () {}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.style-loader.useable.pitch"></a>[function <span class="apidocSignatureSpan">style-loader.useable.</span>pitch (remainingRequest)](#apidoc.element.style-loader.useable.pitch)
- description and source-code
```javascript
pitch = function (remainingRequest) {
	if(this.cacheable) this.cacheable();
	var query = loaderUtils.getOptions(this) || {};
	return [
		"var refs = 0;",
		"var dispose;",
		"var content = require(" + loaderUtils.stringifyRequest(this, "!!" + remainingRequest) + ");",
		"if(typeof content === 'string') content = [[module.id, content, '']];",
		"if(content.locals) exports.locals = content.locals;",
		"exports.use = exports.ref = function() {",
		"	if(!(refs++)) {",
		"		dispose = require(" + loaderUtils.stringifyRequest(this, "!" + path.join(__dirname, "addStyles.js")) + ")(content, " + JSON
.stringify(query) + ");",
		"	}",
		"	return exports;",
		"};",
		"exports.unuse = exports.unref = function() {",
		"       if(refs > 0 && !(--refs)) {",
		"		dispose();",
		"		dispose = null;",
		"	}",
		"};",
		"if(module.hot) {",
		"	var lastRefs = module.hot.data && module.hot.data.refs || 0;",
		"	if(lastRefs) {",
		"		exports.ref();",
		"		if(!content.locals) {",
		"			refs = lastRefs;",
		"		}",
		"	}",
		"	if(!content.locals) {",
		"		module.hot.accept();",
		"	}",
		"	module.hot.dispose(function(data) {",
		"		data.refs = content.locals ? 0 : refs;",
		"		if(dispose) {",
		"			dispose();",
		"		}",
		"	});",
		"}"
	].join("\n");
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
