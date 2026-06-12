---
title: "nvidia drivers"
date: 2009-12-29
forum: General Help
---

### Post by arturieto on 2009-12-29
i got this when i install the nvidia driver:

art@art-desktop:~$ sudo apt-get install nvidia-glx-173
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-173
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/7,974kB of archives.
After this operation, 23.6MB of additional disk space will be used.
(Reading database ... 139368 files and directories currently installed.)
Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.20-0ubuntu5_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
y
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-173' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.20-0ubuntu5_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-173_173.14.20-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


please help! ! !

---

### Post by arturieto on 2009-12-30
please help. give me some answers to my woo. ho.ho.ho.ho.

---

### Post by jbrown96 on 2009-12-30
```
sudo apt-get -f install
```

---

### Post by arturieto on 2010-01-01
tried the command, but it doesnt work. any other suggestion!! my friend please help. without this recommended installation of driver (173), i am in low graphic mode.

---

