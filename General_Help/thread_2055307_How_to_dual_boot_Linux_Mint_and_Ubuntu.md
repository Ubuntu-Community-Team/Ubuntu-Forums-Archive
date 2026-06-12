---
title: "How to dual boot Linux Mint and Ubuntu"
date: 2012-09-09
forum: General Help
---

### Post by aligator12 on 2012-09-09
Hi, I have ubuntu 12.04 installed on my entire hard drive. How do I install Linux Mint on a USB drive without hurting ubuntu?

---

### Post by 2F4U on 2012-09-09
The installation is not different from installing on an internal drive. Make sure you take care where you install the boot loader grub. You want the boot loader to go to the MBR of the usb drive, and not to your  internal hard disk. Here is also an article that describes the procedure:

[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

---

### Post by C.S.Cameron on 2012-09-09
It is safest to unplug the internal drive first.

---

### Post by aligator12 on 2012-09-12
Alright I tried to install multiple distros to the usb but they were all really slow. Is there any way to re-partition my hdd to boot both Linux Mint and Ubuntu?

---

