---
title: "Compile simple linux to boot into command line"
date: 2012-06-22
forum: General Help
---

### Post by furmada on 2012-06-22
Hello All,

I am looking to compile a linux kernel that boots into a command line: 

Power on PC
Boot new kernel from USB
load a root shell: root@mykernel# 

First question:
Is this possible?

Second question:
Can I install packages (e.g. python, lxde) from the shell?

Third question:
How should I build the kernel?

Thank You.

---

### Post by LiamOS on 2012-06-22
I am assuming you are asking how to install Ubuntu on a USB stick, as opposed to having your /boot partition on a USB stick or something else.


If you want to do this as an Ubuntu specific installation, here's what I'd recommend trying:

Boot an Ubuntu minimal install CD, and choose to do a command line install. See if you can select to do the installation on the USB drive as opposed to the hard drive, which will likely be listed as /dev/sdb, /dev/sdc or so on. The installation will take care of the kernel and a lot of the dirty work for you, and it can do your partitioning for you if you want. After that, your USB stick will have its own linux environment, able to download things from the repositories and such.



If you want to build a kernel yourself, download the kernel sources from Kernel.org and extract it into a directory for you to work in.
Then 
$ make menuconfig
and when you have it configured to your needs,
# make && make modules_install


If you want a very customised installation, I'd recommend considering Arch linux, as it's fairly nifty at a command line level and has a nice package manager, or Gentoo linux if you want something even better and don't value your time.

---

