---
title: "Problems mounting usb sticks"
date: 2010-06-11
forum: General Help
---

### Post by Sh4wn on 2010-06-11
Hi,

I've installed Ubuntu 10.04 on my dad's computer, to prove Linux is ****ing awesome. He's quite happy, there's only thing that annoys him a lot: USB harddrives/flashsticks don't work properly. In some rare occasions an USB stick mounts itself automaticly, but in most cases it just doesn't do anything. They do show up when using the lsusb command, they don't show up in nautlis under locations. 

When using the fdisk -l, it shows the partition table of the main harddisk, then the program takes a coffeebreak, and after a few minutes he finally gives /dev/sdb1 as the USB flashdrive.

When trying to mount it manually, using mount /dev/sdb1 it takes a few minutes and after a while it gives the error:
Error mounting: mount: /dev/sdb1: can't read superblock

Things I tried:
Installing pmount and libpmount0.0, I think this actually did improve the situation a bit, as it now actually gives an error message, and sometimes a usb flashdrive actually does get mounted.

I also removed HAL, but nothing changed. I've also checked if floppy drive was enabled in BIOS, but couldn't find anything that would lead to such setting..

And now, I'm stuck. Is it a hardware problem? I've connected an USB mouse and keyboard, and they both work properly, and my USB connected printer also.. What could be the problem?

---

