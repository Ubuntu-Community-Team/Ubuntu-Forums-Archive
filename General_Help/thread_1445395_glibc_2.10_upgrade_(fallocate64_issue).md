---
title: "glibc 2.10 upgrade (fallocate64 issue)"
date: 2010-04-02
forum: General Help
---

### Post by subvertbeats on 2010-04-02
Hi

Im trying to compile rtorrent, and the config.log is showing:

```

...
configure:15852: checking for XMLRPC-C
configure:15886: g++ -o conftest -g -O2 -g -DDEBUG -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include     -I/usr/local/include   -I/usr/local/include    conftest.cpp -lncursesw  -lsigc-2.0   -lcurl   -L/usr/local/lib -ltorrent   -L/usr/local/lib   -lxmlrpc_server -lxmlrpc -lxmlrpc_util -lxmlrpc_xmlparse -lxmlrpc_xmltok  >&5
/usr/local/lib/libtorrent.so: undefined reference to `fallocate64'
...
```

Ive discovered that there are issues with fallocate64 in the 2.10 versions of glibc and related packages.
The issues are solved in the 2.11 versions.

Im pretty new to all this, and wondering how to proceed.
I did try downloading all the relevant packages manually from here: [http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/](http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/), and installing them, but ended up in dependency hell.
I managed to get everything back to the state it was before.

Can anyone advise how I can successfully compile rtorrent given this issue?

---

### Post by subvertbeats on 2010-04-03
I ended up upgrading to the lucid beta, it seemed the route of least resistance

---

