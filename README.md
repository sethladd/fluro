<img src="https://storage.googleapis.com/app-logos/logo_fluro.png" width="220">
<br/><br/>

The brightest, hippest, coolest router for Flutter.

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://pub.dartlang.org/packages/fluro)
[![Build Status](https://travis-ci.org/goposse/fluro.svg?branch=master)](https://travis-ci.org/goposse/fluro)
[![Coverage](https://codecov.io/gh/goposse/fluro/branch/master/graph/badge.svg)](https://codecov.io/gh/goposse/fluro)

## Features

- Simple route navigation
- Wildcard parameter matching
- Querystring parameter parsing
- Common transitions built-in
- Simple custom transition creation

## Getting started

You should ensure that you add the router as a dependency in your flutter project.
```yaml
dependencies:
 fluro: "^1.0.0"
```

You can also reference the git repo directly if you want:
```yaml
dependencies:
 fluro:
   git: git://github.com/goposse/fluro.git
```


You should then run `flutter packages upgrade` or update your packages in IntelliJ.

## Example Project

There is a pretty sweet example project in the `example` folder. Check it out. Otherwise, keep reading to get up and running.

## Setting up

First, you should define a new `Router` object by initializing it as such:
```dart
final Router router = new Router();
```
It may be convenient for you to store the router globally/statically so that
you can access the router in other areas in your application.

After instantiating the router, you will need to define your routes and your route handlers:
```dart
RouteHandler usersHandler = (Map<String, String> params) {
  return new UsersScreen(params["id"]);
};

void defineRoutes(Router router) {
  router.define("/users/:id", handler: usersHandler);
}
```

In the above example, the router will intercept a route such as
`/users/1234` and route the application to the `UsersScreen` passing
the value `1234` as a parameter to that screen.

## Navigating

You can use the `Router` with the `MaterialApp.onGenerateRoute` parameter
via the `Router.generator` function. To do so, pass the function reference to
the `onGenerate` parameter like: `onGenerateRoute: router.generator`.

You can then use `Navigator.push` and the flutter routing mechanism will match the routes
for you.

You can also manually push to a route yourself. To do so:

```dart
router.navigateTo(context, "/users/1234",
    transition: TransitionType.fadeIn);
```
<br/>
<hr/>
Fluro is a Posse Production.
<br/>
<a href="http://goposse.com" target="_posse">
<img src="https://storage.googleapis.com/posse-logos/logo-posse.png"
  width="60"></a>
