Heroku Buildpack: Geo
=====================

Heroku Buildpack Geo is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) that
installs the Geo/GIS libraries [GDAL](https://www.gdal.org/), [GEOS](https://trac.osgeo.org/geos/) and [PROJ](https://proj4.org/)

It can be used to get [GeoDjango](https://docs.djangoproject.com/en/2.1/ref/contrib/gis/) or [RGeo](https://github.com/rgeo/rgeo) running on Heroku.

Usage
-----

This buildpack is designed to be used in combination with other buildpacks by using Heroku's [multiple buildpack support](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app).

Ensure that Heroku Buildpack Geo is the first buildpack on your list of buildpacks:

```
$ heroku buildpacks
=== Buildpack URLs
1. https://github.com/heroku/heroku-geo-buildpack.git
2. heroku/python
```

Default Versions
----------------

The buildpack will install the following version by default:

GDAL - 2.4.0</br>
GEOS - 3.7.2</br>
PROJ - 5.2.0</br>

You can change the version of each library that will be installed by setting the `GDAL_VERSION`, `GEOS_VERSION` or `PROJ_VERSION` config variables.

Migrating from heroku/python GEOs support
-----------------------------------------

If you were previously using the undocumented `BUILD_WITH_GEO_LIBRARIES` functionality of the official [Heroku Python Buildpack](https://github.com/heroku/heroku-buildpack-python) here are instructions for changing to this buildpack:

1. You have to completely remove the `BUILD_WITH_GEO_LIBRARIES` config variable like so - `heroku config:unset BUILD_WITH_GEO_LIBRARIES`
2. You should consider flushing your applications build cache by following these instructions - https://help.heroku.com/18PI5RSY/how-do-i-clear-the-build-cache