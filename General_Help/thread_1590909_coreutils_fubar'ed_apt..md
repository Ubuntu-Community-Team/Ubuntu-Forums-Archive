---
title: "coreutils fubar'ed apt."
date: 2010-10-08
forum: General Help
---

### Post by stormcoder on 2010-10-08
I had an upgrade come through on update-manager the other day the included /coreutils_7.4-2ubuntu3_amd64.deb. The installation locked up when it hit this file. Ever since that day I can't install anything else without apt trying to install /coreutils_7.4-2ubuntu3_amd64.deb first thing and of course it continues to lock up apt-get. I have to kill -9 apt-get because control-C doesn't work. I've tried several ways to try and get around this but nothing works so far. Everytime it locks up I have to go around and remove lock files and run sudo dpkg --configure -a. Anyone have a workaround for this?

I'm on 10.04 x64. Multi-Core workstation.

Apt output

> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  coreutils cups-driver-gutenprint dmsetup fglrx-modaliases gdm
  libcouchdb-glib-1.0-2 libdesktopcouch-glib-1.0-2 libdevmapper-event1.02.1
  libdevmapper1.02.1 libgksu2-0 libgssapi-krb5-2 libgutenprint2 libk5crypto3
  libkrb5-3 libkrb5support0 libssl0.9.8 lvm2 nspluginwrapper openssl
  python-imaging screen tar
22 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2,907kB/9,511kB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main coreutils 7.4-2ubuntu3 [2,907kB]
Fetched 2,907kB in 3s (729kB/s)      
Preconfiguring packages ...
(Reading database ... 250781 files and directories currently installed.)
Preparing to replace coreutils 7.4-2ubuntu2 (using .../coreutils_7..4-2ubuntu3_amd64.deb) ...
Unpacking replacement coreutils ...


---

### Post by moushkka on 2010-12-19
It seems like I've got the same problem.
Did you ever figure out a workaround?

---

