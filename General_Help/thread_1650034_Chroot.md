---
title: "Chroot"
date: 2010-12-21
forum: General Help
---

### Post by Mecasickle on 2010-12-21
Hey guys. 

I've just got an Alienware m11x laptop. Installed the  Netbook Ubuntu Linux 10.10 version for my laptop. EVerything worked fine  untill I agreed on my update manager and upgraded everything selected.  As a result on my next booting session I had a problem when trying to  access to my 2.6.35-22-kernel or 2.6.35-23-generic kernel.

Now I am having chroot problems,  when I do the following steps:

1)Boot from liveCD / (Live USB stick in my case)

2) sudo fdisk -l ( to check my partitions, ?I guess the onw I'm using is /dev/sda2 because it has a star on it)
3) sudo mkdir /media/newroot
4) sudo mount /dev/sda2 /media/newroot
5) sudo chroot /media/newroot (HERE IS WHERE I GET MY PROBLEM!!)

Then I 'm supposed to execute these steps:

6) sudo update-initramfs -u -k 2.6.35-22-generic
7) reboot.

The error I get when using the chroot command is:
chroot: failed to run command `/bin/bash': No such file or directory

Any ideas or points I'm missing out?
For Ubuntu 10.10, and using a USB stick to boot.

---

### Post by Mecasickle on 2010-12-21
Also having this problem:

root@ubuntu:/home/ubuntu# update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
cp: cannot stat `/vmlinuz': No such file or directory


When using the alternate solution to fix the main problem :

udevadm trigger is not permitted while udev is unconfigured

I've checked most of the threads regarding this problem and all of them said that I should use the Chroot solutoin (that hasnt worked) or the "update-initramfs -u -k all" sollution, that also produces an error.

Any thing I'm missing?
Thanks!

---

### Post by HermanAB on 2010-12-21
Howdy,

Why are you using chroot anyway?  It is mostly a waste of time, since it doesn't really provide serious security.

---

### Post by Mecasickle on 2010-12-21
It started out on trying to fix this problem:

**udevadm trigger is not permitted while udev is unconfigured** 
(On booting time , and ubuntu fails to boot).

And using chroot was one of the solutiosn to fix it. But chrrot isn't really working for me ... :(

Maybe there's another way out?

---

