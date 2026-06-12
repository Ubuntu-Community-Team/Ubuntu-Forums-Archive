---
title: "Target filesystem doesn't have /sbin/init. and more."
date: 2010-11-15
forum: General Help
---

### Post by dgary123 on 2010-11-15
Hi there,

I hope that you will be able to help me. I know that my topic may seem the same as some other threads, but there is a twist and it seems that I can't sort things out.

I installed Ubuntu on the family's 4 year old Dell about a year ago when Windows stopped working (too many bluescreens!). It seed to be good, until one day when I tried to boot and it listed some codes on a black screen. I then reinstalled ubuntu from one of my disks, and it worked fine... until the entire thing occurred again a week later. This happened once or twice more, until today's problem:

It won't boot into ubuntu and also has white writing on the black background (read this below). I tried to reinstall from a ubuntu install disk, burned additional install disks, made an install usb, and also tried opensuse. They all say the below message when I try to boot into the disk:

lots of code..............

Killed
mount: mounting on /dev on root/dev failed: No such file or directory
mount: mounting on /sys on root/sys failed: No such file or directory
mount: mounting on /proc on root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs) [        2.712287] ieee1394 host added: ID: BUS[0-00:1023] GUID[464fc00
00b924121].


Thank you all for any help that you can provide!
Daniel

---

### Post by TeoBigusGeekus on 2010-11-15
Hm... could it be a failing hd?
Try to boot from a live cd, go to terminal and fsck all your partitions for errors.

---

### Post by dgary123 on 2010-11-15
> **TeoBigusGeekus said:**
> Hm... could it be a failing hd?
Try to boot from a live cd, go to terminal and fsck all your partitions for errors.
 
Hi,
Thanks for your response. It may be a failing hard drive, but I'm not too sure.
Is the live cd ISO the same that is distributed on the ubuntu website?
If not, can you please link to it?
 
I tried google chrome os on a flash drive, and it worked! Not sure how though and it's not a permanent solution. Other linux distros didn't work.
 
Daniel

---

### Post by tk189 on 2010-11-16
It's unlikely to be a failing hard drive as this very same problem is affecting users all over the place. There are multiple threads on these forums about this issue.

I have been plagued by these crashes and reboot errors since I first began using linux in the form of ubuntu 10.04 and recently 10.10 I must say the fact this problem basically makes my PC pretty much unusable for anything remotely serious like work (i'm a freelance web designer) and is a shame as i really like the sytem overall.

Do a seasrch for the keyword [BOOTARG]("http://ubuntuforums.org/search.php?searchid=77449188") on these forums and see just how many folks are affected by it. It isn't going away yet and all I can do is purge and re-install grub via a liveCD session several times daily. I don't want to go back to Windows I really don't but I may be forced to if this seriously shabby boot thing isn't resolved soon.

:confused:

---

