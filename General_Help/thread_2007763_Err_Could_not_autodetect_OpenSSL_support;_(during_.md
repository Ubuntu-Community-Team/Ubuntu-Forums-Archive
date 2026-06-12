---
title: "Err: Could not autodetect OpenSSL support; (during installin nodjs.org)"
date: 2012-06-21
forum: General Help
---

### Post by SidebySide on 2012-06-21
I need **[COLOR=Sienna]node[/COLOR]** and **[COLOR=Sienna]jshint[/COLOR]** for [Bootstrap Less]("http://twitter.github.com/bootstrap").
I tried to install [https://nodeload.github.com/isaacs/nave/tarball/master](https://nodeload.github.com/isaacs/nave/tarball/master) using below command:
```
sudo bash nave.sh 

npm install jshint
```Command output:
```

[FONT=Garamond]npm ERR! [COLOR=Red]Error: [node.js]("http://nodejs.org/dist/v0.6.19/node-v0.6.19.tar.gz") not compiled with **openssl** crypto support[/COLOR].
npm ERR!     at tls.js:50:9
npm ERR!     at NativeModule.compile (node.js:542:5)
npm ERR!     at Function.require (node.js:510:18)
npm ERR!     at Function._load (module.js:296:25)
npm ERR!     at Module.require (module.js:359:17)
npm ERR!     at require (module.js:375:17)
npm ERR!     at Object.<anonymous> (/usr/local/lib/node_modules/npm/node_modules/request/forever.js:7:11)
npm ERR!     at Module._compile (module.js:446:26)
npm ERR!     at Object..js (module.js:464:10)
npm ERR!     at Module.load (module.js:353:31)
npm ERR! You may report this log at:
npm ERR!     <http://github.com/isaacs/npm/issues>
npm ERR! or email it to:
npm ERR!     <npm-@googlegroups.com>
npm ERR! 
npm ERR! System Linux 2.6.32-21-generic
npm ERR! command "node" "/usr/local/bin/npm" "install" "jshint"
npm ERR! cwd /home/quark/Desktop/isaacs-nave-341c32b
npm ERR! node -v v0.6.19
npm ERR! npm -v 1.1.24
npm ERR! message node.js not compiled with openssl crypto support.
npm ERR! 
npm ERR! Additional logging details can be found in:
npm ERR!     /home/quark/Desktop/isaacs-nave-341c32b/npm-debug.log
npm not ok
npm not ok
```

[/FONT]How should I install OpenSSl development Packages?
when I type openssl in terminal, I get this:
[FONT=Garamond]side@BYSIDE:/$ openssl
OpenSSL> [/FONT]
[FONT=Garamond][/FONT]

---

### Post by SidebySide on 2012-06-22
Bump...

---

### Post by SidebySide on 2012-06-27
How should I install OpenSSL development packages?

---

### Post by SidebySide on 2012-06-28
How many times should I bump?!
:'(

---

