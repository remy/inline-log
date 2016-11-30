# Inline log

I wrote a tiny (potentially naff) logger thing that captures all `stdout` and `stderr` and logs in realtime to the browser (using server sent events).

Kinda inspired by the way [Zeit's now](https://zeit.co/now) shows you a loading screen during deployment, but I wanted to get at the stdout logging on my now instances (since you don't have this functionality at the moment).

## Install

Firslty get the module: `npm i -s inline-log`, then in your http server (I'm using Express below):

```js
app.use('/_logger', require('inline-log')({ limit: 50 }))
```

That'll capture all the stdout/err and when you visit http://my-site.com/_logger it'll put your logs on the screen (with the last 50 lines). Obviously you can add auth or stuff before the middleware too.