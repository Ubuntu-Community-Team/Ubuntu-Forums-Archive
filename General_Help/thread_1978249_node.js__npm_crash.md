---
title: "node.js / npm crash"
date: 2012-05-11
forum: General Help
---

### Post by lykwydchykyn on 2012-05-11
I use node-js to run jslint with emacs, so that I can get real-time error checking on my javascript code.

After upgrading to precise, it stopped working and gave me an error.

I tried to reinstall using npm, but every time I get this crash:
```

node.js:201
        throw e; // process.nextTick error, or 'error' event on first tick
              ^
Error: require.paths is removed. Use node_modules folders, or the NODE_PATH environment variable instead.
    at Function.<anonymous> (module.js:378:11)
    at Object.<anonymous> (/home/alanm/.node_libraries/nopt@1.0.10/index.js:4:21)
    at Module._compile (module.js:441:26)
    at Object..js (module.js:459:10)
    at Module.load (module.js:348:32)
    at Function._load (module.js:308:12)
    at Module.require (module.js:354:17)
    at require (module.js:370:17)
    at Object.<anonymous> (/usr/share/npm/lib/utils/ini.js:36:12)
   at Module._compile (module.js:441:26)

```

If I attempt to run jslint (it's still installed from before the upgrade), I get a similar error:

```


node.js:201
        throw e; // process.nextTick error, or 'error' event on first tick
              ^
Error: require.paths is removed. Use node_modules folders, or the NODE_PATH environment variable instead.
    at Function.<anonymous> (module.js:378:11)
    at Object.<anonymous> (/usr/local/bin/jslint@0.1.0:4:21)
    at Module._compile (module.js:441:26)
    at Object..js (module.js:459:10)
    at Module.load (module.js:348:32)
    at Function._load (module.js:308:12)
    at Array.0 (module.js:479:10)
    at EventEmitter._tickCallback (node.js:192:41)

```

It looks similar to this bug:
[https://bugs.launchpad.net/ubuntu/+source/npm/+bug/920127](https://bugs.launchpad.net/ubuntu/+source/npm/+bug/920127)

Does anyone else have this problem, and know a workaround?

---

### Post by lykwydchykyn on 2012-05-11
Never mind; I just had to delete the jslint files from /usr/local/bin and the old files from ~/.node_libraries and then I could reinstall via npm.

---

