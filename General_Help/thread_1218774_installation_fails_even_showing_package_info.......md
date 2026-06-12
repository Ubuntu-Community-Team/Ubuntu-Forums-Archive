---
title: "installation fails even showing package info......."
date: 2009-07-21
forum: General Help
---

### Post by abhilashm86 on 2009-07-21
i tried installing bzr( version control system), i tried syaptic and also terminal, but why does install just stops after showing package information....
```

abhilash@abhilash:~$ sudo apt-get install bzr-gtk
[sudo] password for abhilash: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bzr-gtk
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
1 not fully installed or removed.
Need to get 165kB of archives.
After this operation, 1139kB of additional disk space will be used.
Err http://in.archive.ubuntu.com hardy/universe bzr-gtk 0.93.0-1
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/universe/b/bzr-gtk/bzr-gtk_0.93.0-1_all.deb  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```
when checked /etc/apt/sources.list, no problem?? what is error and how to recover??

---

### Post by jenkinbr on 2009-07-21
It seems you may be out of date.  run in a terminal ```
sudo apt-get update
sudo apt-get upgrade
```

Once this is done, try again.

---

