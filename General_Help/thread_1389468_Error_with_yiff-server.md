---
title: "Error with yiff-server"
date: 2010-01-24
forum: General Help
---

### Post by Nai on 2010-01-24
I just reinstalled Ubuntu a couple days ago (after about a month of not having it) and for the most part reinstallation and reconfiguration and such have been going well. Suddenly this morning, though, I started getting errors every time I tried to install or uninstall any package in the Software Center. It reads:

> Package operation failed
The installation or removal of a software package failed.

and when I click on the details button I get this:

installArchives() failed: Selecting previously deselected package dkms.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 341404 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.0.1-0ubuntu1_all.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from .../fglrx-kernel-source_2%3a8.660-0ubuntu4_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.660-0ubuntu4_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.660-0ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Setting up yiff-server (2.14.5-5.1) ...
Starting Y Sound Server: invoke-rc.d: initscript yiff-server, action "start" failed.
dpkg: error processing yiff-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up dkms (2.1.0.1-0ubuntu1) ...
 * Running DKMS auto installation service for kernel 2.6.31-17-generic-pae
   ...done.

Setting up fglrx-kernel-source (2:8.660-0ubuntu4) ...
Loading new fglrx-8.660 DKMS files...
First Installation: checking all kernels...
Building initial module for 2.6.31-17-generic-pae, architecture -a i686
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-17-generic-pae/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Setting up xorg-driver-fglrx (2:8.660-0ubuntu4) ...

Setting up fglrx-amdcccle (2:8.660-0ubuntu4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 yiff-server

It seems to still install the programs, but I'm not sure if they will work correctly or not. Is there a way to fix this?

---

### Post by Ichido on 2010-12-22
This worked for me:

Uninstall yiff server in synaptic.. no errors now..

---

