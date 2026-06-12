---
title: "Less.js (lessCss) issues"
date: 2012-05-08
forum: General Help
---

### Post by crptonx on 2012-05-08
Hi there,

I'm having some trouble getting less to work (compiler, not the in browser parser). Basically, the error I'm getting gives me the impressions that node can't find it (when using the console) and that the binary is not installed ('lessc' used from bash)... here's my term output:

```

[COLOR=#000000][FONT=Arial]xxx@xxx:~/less_files$ lessc test.less > out.css

node.js:249
        throw e; // process.nextTick error, or 'error' event on first tick
              ^
Error: Cannot find module 'less'
    at Function._resolveFilename (module.js:333:15)
    at Function._load (module.js:280:25)
    at Module.require (module.js:357:17)
    at require (module.js:373:17)
    at Object. (/usr/bin/lessc:7:12)
    at Module._compile (module.js:444:26)
    at Object..js (module.js:462:10)
    at Module.load (module.js:351:32)
    at Function._load (module.js:309:12)
    at module.js:482:10
xxx@xxx:~/less_files$ node
> var less = require('less');
undefined
> [/FONT][/COLOR]

```To show that it is installed via npm...

```

[COLOR=#000000][FONT=Arial]~$ npm install less[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]npm http GET https://registry.npmjs.org/less[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]npm http 200 https://registry.npmjs.org/less[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]npm http GET https://registry.npmjs.org/less/-/less-1.3.0.tgz[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]npm http 200 https://registry.npmjs.org/less/-/less-1.3.0.tgz[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]less@1.3.0 ./node_modules/less[/FONT][/COLOR]

```bin installed via apt-get....
```

[COLOR=#000000][FONT=Arial]…[some items omitted][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]node-less is already the newest version.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.[/FONT][/COLOR]

```I'm pretty new to node and npm, so I'm unsure of where to go from here. If someone could point me in theright direction, I'd appreciate it.

Thanks.

---

