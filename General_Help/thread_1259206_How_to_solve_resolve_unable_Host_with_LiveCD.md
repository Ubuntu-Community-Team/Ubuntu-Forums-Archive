---
title: "How to solve resolve unable Host with LiveCD"
date: 2009-09-06
forum: General Help
---

### Post by sunseeker888 on 2009-09-06
Hi Guys


I am using LiveCD to try to repair ubuntu, but it's unable to resolve host?


I do not what to do.


I could try to edit /etc/hosts, but do not know what to add.

---

### Post by hal10000 on 2009-09-06
If you setup your network with dhcp you would not need to edit /etc/hosts, unless you want to get access to some machines on your local network.
I assume you want to get an internet connection, is this right?
If so, then you should just run network-manager.

What kind of repair-work are you trying to do?
If you want e.g. to repair packages on your ubuntu-system (on the harddisk), then you probably have to work in a chroot environment

---

