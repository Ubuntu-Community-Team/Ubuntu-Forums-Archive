---
title: "Trying to run Trine on Ubuntu 12.04, says GLIBCXX not found"
date: 2012-05-05
forum: General Help
---

### Post by mendhak on 2012-05-05
I am attempting to run a game called 'Trine' on Ubuntu 12.04.  When I run it, it fails with this message:

> 
mendhak@COFFEE:~/Programs/trine$ ./trine-launcher

**./lib32/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/i386-linux-gnu/libproxy.so.1)**

**Failed to load module: /usr/lib/i386-linux-gnu/gio/modules/libgiolibproxy.so**

./trine-launcher32: symbol lookup error: /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0: undefined symbol: _XGetRequest


All of the files mentioned above exist.  Presumably 12.04 has some newer version of GLIBCXX.  How do I point to the version that it is looking for?

---

### Post by srikad8 on 2012-06-16
Try This:

```
 sudo apt-get install libtxc-dxtn-s2tc0 

```

---

