Redux pattern implemented in RxJS
=====

This is a sample project / tutorial that demonstrates how to implement the Redux pattern (i.e. for usage with React) in TypeScript using only [RxJS v5](https://github.com/ReactiveX/rxjs) inspired by the blog post by [Michael Zalecki](http://michalzalecki.com/use-rxjs-with-react/).

Advantages
-----

* __Typed actions by default__: No need for [FSA](https://github.com/acdlite/flux-standard-action) or magic string constants; all actions are implemented using the `.next()` and `.error()` methods on typed `Rx.Subject`s.
* No need for endless `switch` statements
* Almost __[no boilerplate code](https://github.com/Dynalon/redux-pattern-with-rx/blob/master/src/rxjs-redux.ts)__, no dependencies other than RxJS using only the `map`, `merge`, `scan` and `publishReplay` operators.

How to build
----

1. Clone this repo
1. `npm install`
1. `npm run build`
1. Run a webserver from the `dist` folder for testing

Notes
----

* Unfortunately, TypeScript does not yet support the [ES7 object spread operator](https://github.com/sebmarkbage/ecmascript-rest-spread): ` state => { ...state, prop: newProp }; ` which is why I use `state = Object.assign(state, { prop: newProp })` instead. But since `Object.assign` is an ES6 feature, you might need to add a polyfill [depending on your targeted browser matrix](http://kangax.github.io/compat-table/es6/#test-Object_static_methods_Object.assign) or replace it with a deep clone function that might ship with your favorite framework such as `jQuery.extend` or `angular.copy`.
* Webpack is used as a module bundler, but the pattern will also work using other module bundlers or typescript module outputs.
