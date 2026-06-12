---
title: "Can't install anything in 12.04"
date: 2012-04-30
forum: General Help
---

### Post by bmartin on 2012-04-30
I did a fresh install of 12.04 on release day. Everything was going fine until now.

I can't install anything anymore. When I run apt from the command line, it aborts.
```
blake@blake-desktop:~$ sudo apt-get install wesnoth-1.10
[sudo] password for blake: 
Reading package lists... Done
blake@blake-desktop:~$ e... 0%
```

I've tried **apt-get install -f** and **dpkg --reconfigure -a**, but neither of them seem to do anything.

If I open the Ubuntu software center, it experiences a segmentation fault.

Any ideas?

---

### Post by bmartin on 2012-04-30
I figured it out... rm -f /var/cache/apt/*.bin

This deletes the package cache. Apparently, it doesn't replace the cache when you run **apt-get update**.

---

