---
title: "nfs-kernel-server removes rpcbind??"
date: 2012-08-15
forum: General Help
---

### Post by wardrive on 2012-08-15
Hi, I'm trying to setup an nfs server, and wherenever I try to install rpcbind, it removes the nfs-kernel-server or the other way around. I'm installing on ubuntu 10.04 Server and trying to setup cloudstack ( that's why I'm not using 12.04 server ). Does anybody have an idea why nfs won't install with rpcbind???

---

### Post by HermanAB on 2012-08-16
$ sudo apt-get --no-remove yaddayadda

---

### Post by karrika on 2012-11-22
> **HermanAB said:**
> $ sudo apt-get --no-remove yaddayadda

apt-get --no-remove install rpcbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nfs-common nfs-kernel-server portmap
The following NEW packages will be installed:
  rpcbind
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Packages need to be removed but remove is disabled.

Next idea?

---

