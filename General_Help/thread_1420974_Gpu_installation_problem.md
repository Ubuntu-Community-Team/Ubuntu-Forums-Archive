---
title: "Gpu installation problem"
date: 2010-03-03
forum: General Help
---

### Post by nafeez on 2010-03-03
please help me... i m new in linux platform and facing gpu installation problem in ubuntu 9.10 . 

i'v downloaded a driver for my ati radeon graphics card ati-driver-installer-10-2-x86.x86_64.run  .i created .dev files of that driver. after giving the command
sudo dpkg -i *.deb (in terminal)

it shows>
=========
nafeez@ubuntu:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package fglrx-amdcccle.
(Reading database ... 116431 files and directories currently installed.)
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.702-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.702-0ubuntu1_i386.deb) ...
Preparing to replace fglrx-modaliases 2:8.702-0ubuntu1 (using fglrx-modaliases_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Preparing to replace libamdxvba1 2:8.702-0ubuntu1 (using libamdxvba1_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement libamdxvba1 ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.702-0ubuntu1_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.702-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx-kernel-source (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.702-0ubuntu1) ...
Setting up libamdxvba1 (2:8.702-0ubuntu1) ...

dpkg: dependency problems prevent configuration of xorg-driver-fglrx:
 xorg-driver-fglrx depends on fglrx-kernel-source; however:
  Package fglrx-kernel-source is not configured yet.
dpkg: error processing xorg-driver-fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg-driver-fglrx-dev:
 xorg-driver-fglrx-dev depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing xorg-driver-fglrx-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for sreadahead ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx-kernel-source
 xorg-driver-fglrx
 xorg-driver-fglrx-dev
 fglrx-amdcccle
nafeez@ubuntu:~/Desktop$ 
======

why its showing those errors?
again i typed
=========
nafeez@ubuntu:~/Desktop$ aticonfig --initial
Unable to open /etc/ati/control, please reinstall the driver.
aticonfig: No supported adapters detected
=========
but my card model is supported. HD2600 XT, 2600 series is supported. what can I do? plz help.

---

### Post by gsmanners on 2010-03-03
For some reason, you don't have dkms installed. The rest is failing like dominoes falling. Sorry, ATI drivers can be a pain to install and configure.

---

### Post by nafeez on 2010-03-04
Dkms ? is it a update file? how can I install it? (sorry for asking silly question,I m very much new in Linux OS)

is there any alternative solution to install ATI cards? also I didn't find any kind of device manager like windows in u 9.10.

o! one more question to ask... can i enable visual effects with built in (bogus) Intel GMA x3100?

---

### Post by gsmanners on 2010-03-04
To install dkms, type the following:

sudo apt-get install dkms

See: [https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

Intel is not well-supported at the moment. People have reported highly variable success with that company's video cards right now.

---

### Post by nafeez on 2010-03-04
:( i'v installed dkms and it installed successfully.
but graphics card not detected....

if i want to config ati>>
=====================================
nafeez@ubuntu:~$ aticonfig --initial
Could not find configuration file, so create an empty one
Failed to create empty configuration file
===================================
if I click on ATI catalyst control canter from system>preference it shows-

[IMG]http://nafeez4u.hexat.com/ALL%20IMAGES/Screenshot.png[/IMG]

can it be possible that its showing error because i m using new driver?

---

### Post by gsmanners on 2010-03-04
You need to configure in root, so:

sudo aticonfig --initial

---

### Post by nafeez on 2010-03-05
yah, i used that command actually....

---

