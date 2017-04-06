# api documentation for  [geocoder (v0.2.3)](https://github.com/wyattdanger/geocoder)  [![npm package](https://img.shields.io/npm/v/npmdoc-geocoder.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-geocoder) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-geocoder.svg)](https://travis-ci.org/npmdoc/node-npmdoc-geocoder)
#### node wrapper around google's geocoder api

[![NPM](https://nodei.co/npm/geocoder.png?downloads=true)](https://www.npmjs.com/package/geocoder)

[![apidoc](https://npmdoc.github.io/node-npmdoc-geocoder/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-geocoder_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-geocoder/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-geocoder/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-geocoder/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Stephen Wyatt Bush",
        "email": "stephen.wyatt@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/wyattdanger/geocoder/issues"
    },
    "dependencies": {
        "request": "^2.75.0",
        "underscore": "1.3.3",
        "xml2js": "0.2.0"
    },
    "description": "node wrapper around google's geocoder api",
    "devDependencies": {},
    "directories": {},
    "dist": {
        "shasum": "9d1e3165387de505179acf0ae87802fb0008f79c",
        "tarball": "https://registry.npmjs.org/geocoder/-/geocoder-0.2.3.tgz"
    },
    "gitHead": "9af4c80635ede9729a2523bbe9938cf89e064650",
    "homepage": "https://github.com/wyattdanger/geocoder",
    "keywords": [
        "google",
        "geocode",
        "geonames",
        "reverse geocode"
    ],
    "license": {
        "type": "Apachev2",
        "url": "http://www.apache.org/licenses/LICENSE-2.0"
    },
    "main": "./index.js",
    "maintainers": [
        {
            "name": "wyattdanger",
            "email": "stephen.wyatt@gmail.com"
        }
    ],
    "name": "geocoder",
    "optionalDependencies": {
        "xml2js": "0.2.0"
    },
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/wyattdanger/geocoder.git"
    },
    "scripts": {},
    "version": "0.2.3"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module geocoder](#apidoc.module.geocoder)
1.  object <span class="apidocSignatureSpan">geocoder.</span>geonames
1.  object <span class="apidocSignatureSpan">geocoder.</span>providerObj
1.  object <span class="apidocSignatureSpan">geocoder.</span>providerOpts
1.  object <span class="apidocSignatureSpan">geocoder.</span>yahoo
1.  string <span class="apidocSignatureSpan">geocoder.</span>provider

#### [module geocoder.geonames](#apidoc.module.geocoder.geonames)
1.  [function <span class="apidocSignatureSpan">geocoder.geonames.</span>geocode ( providerOpts, loc, cbk, opts )](#apidoc.element.geocoder.geonames.geocode)
1.  [function <span class="apidocSignatureSpan">geocoder.geonames.</span>reverseGeocode ( providerOpts, lat, lng, cbk, opts )](#apidoc.element.geocoder.geonames.reverseGeocode)

#### [module geocoder.providerObj](#apidoc.module.geocoder.providerObj)
1.  [function <span class="apidocSignatureSpan">geocoder.providerObj.</span>geocode ( providerOpts, loc, cbk, opts )](#apidoc.element.geocoder.providerObj.geocode)
1.  [function <span class="apidocSignatureSpan">geocoder.providerObj.</span>reverseGeocode ( providerOpts, lat, lng, cbk, opts )](#apidoc.element.geocoder.providerObj.reverseGeocode)

#### [module geocoder.yahoo](#apidoc.module.geocoder.yahoo)
1.  [function <span class="apidocSignatureSpan">geocoder.yahoo.</span>geocode ( providerOpts, loc, cbk, opts )](#apidoc.element.geocoder.yahoo.geocode)
1.  [function <span class="apidocSignatureSpan">geocoder.yahoo.</span>reverseGeocode ( providerOpts, lat, lng, cbk, opts )](#apidoc.element.geocoder.yahoo.reverseGeocode)



# <a name="apidoc.module.geocoder"></a>[module geocoder](#apidoc.module.geocoder)



# <a name="apidoc.module.geocoder.geonames"></a>[module geocoder.geonames](#apidoc.module.geocoder.geonames)

#### <a name="apidoc.element.geocoder.geonames.geocode"></a>[function <span class="apidocSignatureSpan">geocoder.geonames.</span>geocode ( providerOpts, loc, cbk, opts )](#apidoc.element.geocoder.geonames.geocode)
- description and source-code
```javascript
geocode = function ( providerOpts, loc, cbk, opts ) {

  var options = _.extend({q: loc, maxRows: 10, username:providerOpts.username||"demo" }, opts || {});

  request({
    uri:"http://api.geonames.org/searchJSON",
    qs:options
  }, function(err,resp,body) {
    if (err) return cbk(err);
    var result;
    try {
      result = JSON.parse(body);
    } catch (err) {
      cbk(err);
      return;
    }
    cbk(null,result);
  });
}
```
- example usage
```shell
...

###Example:

'''javascript
var geocoder = require('geocoder');

// Geocoding
geocoder.geocode("Atlanta, GA", function ( err, data ) {
  // do something with data
});

// Reverse Geocoding
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
});
...
```

#### <a name="apidoc.element.geocoder.geonames.reverseGeocode"></a>[function <span class="apidocSignatureSpan">geocoder.geonames.</span>reverseGeocode ( providerOpts, lat, lng, cbk, opts )](#apidoc.element.geocoder.geonames.reverseGeocode)
- description and source-code
```javascript
reverseGeocode = function ( providerOpts, lat, lng, cbk, opts ) {

  var options = _.extend({lat:lat, lng:lng, username:providerOpts.username||"demo" }, opts || {});

  request({
    uri:"http://api.geonames.org/extendedFindNearby",
    qs:options
  }, function(err,resp,body) {
    if (err) return cbk(err);

    var parser = new xml2js.Parser();
    parser.parseString(body, function (err, result) {
      if (err) return cbk(err);

      // Transform geonames' structure into something that looks like Google's JSON outpu
      // https://developers.google.com/maps/documentation/geocoding/#JSON
      var googlejson = {
        "status":"OK",
        "results":[
          {
            "address_components":[],
            "formatted_address":"",
            "geometry":{
              "location":{
                "lat":lat,
                "lng":lng
              }
            }
          }
        ]
      };

      if (result.geonames.address) {
        var a = result.geonames.address[0];

        if (a.streetNumber && typeof a.streetNumber[0]=="string")
          googlejson.results[0].address_components.push({
            "long_name":a.streetNumber[0],
            "short_name":a.streetNumber[0],
            "types":["street_number"]
          });

        if (a.street && typeof a.street[0]=="string")
          googlejson.results[0].address_components.push({
            "long_name":a.street[0],
            "short_name":a.street[0],
            "types":["route"]
          });

        if (a.placename && typeof a.placename[0]=="string")
          googlejson.results[0].address_components.push({
            "long_name":a.placename[0],
            "short_name":a.placename[0],
            "types":["locality", "political"]
          });

        if (a.adminName1 && typeof a.adminName1[0]=="string")
          googlejson.results[0].address_components.push({
            "long_name":a.adminName1[0],
            "short_name":a.adminCode1[0],
            "types":[ "administrative_area_level_1", "political" ]
          });

        if (a.adminName2 && typeof a.adminName2[0]=="string")
          googlejson.results[0].address_components.push({
            "long_name":a.adminName2[0],
            "short_name":a.adminCode2[0],
            "types":[ "administrative_area_level_2", "political" ]
          });

        if (a.countryCode && typeof a.countryCode[0]=="string")
          googlejson.results[0].address_components.push({
            "long_name":a.countryCode[0]=="US"?"United States":"",
            "short_name":a.countryCode[0],
            "types":[ "country" ]
          });

        if (a.lat && typeof a.lat[0]=="string")
          googlejson.results[0].geometry.location = {
            "lat":parseFloat(a.lat[0]),
            "lng":parseFloat(a.lng[0])
          }
      }

      if (result.geonames.geoname) {
        // http://www.geonames.org/export/codes.html
        // https://developers.google.com/maps/documentation/geocoding/#Types
        var fcode2google = {
          "ADM1":[ "administrative_area_level_1", "political" ],
          "ADM2":[ "administrative_area_level_2", "political" ],
          "ADM3":[ "administrative_area_level_3", "political" ],
          "ADMD":[ "political"],
          "PPL" :[ "locality"]
        };

        result.geonames.geoname.forEach(function(geoname) {

          // Push only recognized types to results
          if (geoname.fcode[0]=="PCLI") {
            googlejson.results[0].address_components.push({
              "long_name":geoname.name[0],
              "short_name":geoname.countryCode[0],
              "types":[ "country", "political"]
            });

          } else if (fcode2google[geoname.fcode[0]]) {


            googlejson.results[0].address_components.push({
              "long_name":geoname.toponymName[0],
              "short_name":geoname.name[0],
              "types":fcode2google[geoname.fcode[0]]
            });
          }

        });
      }

      // Make a formatted address as well as we can
      var shortNames = {};
      googlejson.results[0].address_components.forEach(func ...
```
- example usage
```shell
...

// Geocoding
geocoder.geocode("Atlanta, GA", function ( err, data ) {
  // do something with data
});

// Reverse Geocoding
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
});

// Setting sensor to true
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
}, { sensor: true });
...
```



# <a name="apidoc.module.geocoder.providerObj"></a>[module geocoder.providerObj](#apidoc.module.geocoder.providerObj)

#### <a name="apidoc.element.geocoder.providerObj.geocode"></a>[function <span class="apidocSignatureSpan">geocoder.providerObj.</span>geocode ( providerOpts, loc, cbk, opts )](#apidoc.element.geocoder.providerObj.geocode)
- description and source-code
```javascript
geocode = function ( providerOpts, loc, cbk, opts ) {

  var options = _.extend({sensor: false, address: loc}, opts || {});
  var uri = "http" + ( options.key ? "s" : "" ) + "://maps.googleapis.com/maps/api/geocode/json"
  request({
    uri: uri,
    qs:options
  }, function(err,resp,body) {
    if (err) return cbk(err);
    var result;
    try {
      result = JSON.parse(body);
    } catch (err) {
      cbk(err);
      return;
    }
    cbk(null,result);
  });
}
```
- example usage
```shell
...

###Example:

'''javascript
var geocoder = require('geocoder');

// Geocoding
geocoder.geocode("Atlanta, GA", function ( err, data ) {
  // do something with data
});

// Reverse Geocoding
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
});
...
```

#### <a name="apidoc.element.geocoder.providerObj.reverseGeocode"></a>[function <span class="apidocSignatureSpan">geocoder.providerObj.</span>reverseGeocode ( providerOpts, lat, lng, cbk, opts )](#apidoc.element.geocoder.providerObj.reverseGeocode)
- description and source-code
```javascript
reverseGeocode = function ( providerOpts, lat, lng, cbk, opts ) {

  var options = _.extend({sensor: false, latlng: lat + ',' + lng}, opts || {});
  var uri = "http" + ( options.key ? "s" : "" ) + "://maps.googleapis.com/maps/api/geocode/json"

  request({
    uri:uri,
    qs:options
  }, function(err,resp,body) {
    if (err) return cbk(err);
    var result;
    try {
      result = JSON.parse(body);
    } catch (err) {
      cbk(err);
      return;
    }
    cbk(null,result);
  });

}
```
- example usage
```shell
...

// Geocoding
geocoder.geocode("Atlanta, GA", function ( err, data ) {
  // do something with data
});

// Reverse Geocoding
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
});

// Setting sensor to true
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
}, { sensor: true });
...
```



# <a name="apidoc.module.geocoder.yahoo"></a>[module geocoder.yahoo](#apidoc.module.geocoder.yahoo)

#### <a name="apidoc.element.geocoder.yahoo.geocode"></a>[function <span class="apidocSignatureSpan">geocoder.yahoo.</span>geocode ( providerOpts, loc, cbk, opts )](#apidoc.element.geocoder.yahoo.geocode)
- description and source-code
```javascript
geocode = function ( providerOpts, loc, cbk, opts ) {

  var options = _.extend({q: loc, flags: "J", appid:providerOpts.appid||"[yourappidhere]" }, opts || {});

  request({
    uri:"http://where.yahooapis.com/geocode",
    qs:options
  }, function(err,resp,body) {
    if (err) return cbk(err);
    var result;
    try {
      result = JSON.parse(body);
    } catch (err) {
      cbk(err);
      return;
    }
    cbk(null,result);
  });
}
```
- example usage
```shell
...

###Example:

'''javascript
var geocoder = require('geocoder');

// Geocoding
geocoder.geocode("Atlanta, GA", function ( err, data ) {
  // do something with data
});

// Reverse Geocoding
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
});
...
```

#### <a name="apidoc.element.geocoder.yahoo.reverseGeocode"></a>[function <span class="apidocSignatureSpan">geocoder.yahoo.</span>reverseGeocode ( providerOpts, lat, lng, cbk, opts )](#apidoc.element.geocoder.yahoo.reverseGeocode)
- description and source-code
```javascript
reverseGeocode = function ( providerOpts, lat, lng, cbk, opts ) {

  var options = _.extend({q: lat+", "+lng, gflags:"R", flags: "J", appid:providerOpts.appid||"[yourappidhere]" }, opts || {});

  request({
    uri:"http://where.yahooapis.com/geocode",
    qs:options
  }, function(err,resp,body) {

    // console.log("[GEOCODER Yahoo API] uri:", "http://where.yahooapis.com/geocode");
    // console.log("[GEOCODER Yahoo API] options:", JSON.stringify(options));
    // console.log("[GEOCODER Yahoo API] body:", body);

    if (err) return cbk(err);

    var result;
    try {
      result = JSON.parse(body);
    } catch (err) {
      cbk(err);
      return;
    }

    // Transform yahoo' structure into something that looks like Google's JSON outpu
    // https://developers.google.com/maps/documentation/geocoding/#JSON
    var googlejson = {
      "status":"OK",
      "results":[
        {
          "address_components":[],
          "formatted_address":"",
          "geometry":{
            "location":{
              "lat":lat,
              "lng":lng
            }
          }
        }
      ]
    };

    if (result.ResultSet.Error !== "0" && result.ResultSet.Error !== 0) {
      console.log("[GEOCODER Yahoo API] ERROR", result.Error, result.ErrorMessage);
      return cbk(result.ResultSet.ErrorMessage);
    }

    var a = null;
    // Yahoo seems to change its response format "randomly". So, sometimes, it there is only one result,
    // it will be in ResultSet.Result, and sometimes, in ResultSet.Results[0]
    if (undefined !== result.ResultSet.Result) {
      a = result.ResultSet.Result;
    }
    else if (result.ResultSet.Results && result.ResultSet.Results.length) {
      a = result.ResultSet.Results[0];
    }

    if (!a) {
      return cbk("Error getting results from Yahoo API");
    }

    if (a.house)
      googlejson.results[0].address_components.push({
        "long_name":a.house,
        "short_name":a.house,
        "types":["street_number"]
      });

    if (a.street)
      googlejson.results[0].address_components.push({
        "long_name":a.street,
        "short_name":a.street,
        "types":["route"]
      });

    if (a.city)
      googlejson.results[0].address_components.push({
        "long_name":a.city,
        "short_name":a.city,
        "types":["locality", "political"]
      });

    if (a.state)
      googlejson.results[0].address_components.push({
        "long_name":a.state,
        "short_name":a.statecode || a.state,
        "types":[ "administrative_area_level_1", "political" ]
      });

    if (a.county)
      googlejson.results[0].address_components.push({
        "long_name":a.county,
        "short_name":a.countycode || a.county,
        "types":[ "administrative_area_level_2", "political" ]
      });

    if (a.country)
      googlejson.results[0].address_components.push({
        "long_name":a.country,
        "short_name":a.countrycode,
        "types":[ "country" ]
      });

    if (a.postal)
      googlejson.results[0].address_components.push({
        "long_name":a.postal,
        "short_name":a.postal,
        "types":[ "postal_code" ]
      });

    if (a.latitude)
      googlejson.results[0].geometry.location = {
        "lat":parseFloat(a.latitude),
        "lng":parseFloat(a.longitude)
      };

    // Make a formatted address as well as we can
    var formatted = [];
    if (a.line1) formatted.push(a.line1);
    if (a.line2) formatted.push(a.line2);
    if (a.line3) formatted.push(a.line3);
    if (a.line4) formatted.push(a.line4);

    googlejson.results[0].formatted_address = formatted.join(", ");

    // console.log("[GEOCODER Yahoo API], calling callback w/", JSON.stringify(googlejson));

    cbk(null, googlejson);
  });

}
```
- example usage
```shell
...

// Geocoding
geocoder.geocode("Atlanta, GA", function ( err, data ) {
  // do something with data
});

// Reverse Geocoding
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
});

// Setting sensor to true
geocoder.reverseGeocode( 33.7489, -84.3789, function ( err, data ) {
  // do something with data
}, { sensor: true });
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
