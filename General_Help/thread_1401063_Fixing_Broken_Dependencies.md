---
title: "Fixing Broken Dependencies"
date: 2010-02-07
forum: General Help
---

### Post by JaxPenguin on 2010-02-07
While trying to get my iPod Touch working with Rhythmbox and Amarok (never did have success) I was trying all kinds of things like installing iFuse and various other packages. Now I'm stuck because every time I try to install something I get errors of broken dependencies and I can't fix them.

Here's the error I'm currently getting:

Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


This is what I get when trying to run apt-get -f install. I've tried removing and purging the packages but nothing seems to be working. Any help would be greatly appreciated.

ETA: Fixed it. Just deleted the packages in a couple of locations along with a couple more and I'm good to go now.

---

