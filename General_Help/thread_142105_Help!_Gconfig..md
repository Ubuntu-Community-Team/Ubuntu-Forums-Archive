---
title: "Help! Gconfig."
date: 2006-03-09
forum: General Help
---

### Post by grim1234 on 2006-03-09
When attempting to use gconfig, I get :

```

make gconfig

  HOSTCC scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:105:23: error: sys/stat.h: No such file or directory
etc..

```

and lots more fixdep errors after that. 

I've got ubuntu 5.10 installed, via c3 (epia), kernel source is 2.6.12.3.

Anyone know how to fix this error? Perhaps I just need a dependancy installed?

Thanks.

--- source is from [ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.tar.bz2](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.tar.bz2)

---

### Post by lamego on 2006-03-09
Why aren't you using the ubuntu linux source that matches your currently installed version ?

---

### Post by grim1234 on 2006-03-09
I was following [https://wiki.ubuntu.xom/ViaEpiaDriHowto](https://wiki.ubuntu.xom/ViaEpiaDriHowto)

```

grim@ubuntu:~/epia-kernel$ sudo apt-cache search kernel-source
Password:
wacom-tools - utilities for wacom tablets and other hid devices
cpad-common - common files to support the Synaptics cPad driver kernel modules
cpad-kernel-source - source for the Synaptics cPad driver
kernel-patch-2.4-lids - LIDS Kernel Patch
kernel-patch-debian-2.4.27 - Debian patches to Linux 2.4.27
kernel-patch-debian-2.6.10 - Debian patches to Linux 2.6.10
kernel-patch-debian-2.6.11 - Debian patches to Linux 2.6.11
kernel-source-2.4.27 - Linux kernel source for version 2.4.27 with Debian patche s
kernel-source-2.6.10 - Linux kernel source for version 2.6.10 with Debian patche s
kernel-source-2.6.11 - Linux kernel source for version 2.6.11 with Debian patche s
kernel-tree-2.4.27 - Linux kernel source tree for building Debian kernel images
kernel-tree-2.6.10 - Linux kernel source tree for building Debian kernel images
kernel-tree-2.6.11 - Linux kernel source tree for building Debian kernel images
lidstools-2.4 - LIDS Admintool
oprofile - system-wide profiler for Linux systems
wacom-kernel-source - source for the wacom binary modules
grim@ubuntu:~/epia-kernel$ uname -r
2.6.12-9-386
grim@ubuntu:~/epia-kernel$


```

^ no source for my kernel? only 2.6.11?

```

grim@ubuntu:~/epia-kernel$ more /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by grim1234 on 2006-03-10
bump - hopelessly optimistic that someone here actually knows enough to help.

---

