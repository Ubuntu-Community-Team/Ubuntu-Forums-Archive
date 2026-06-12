---
title: "GRUB Error 13-Dual Boot Problem"
date: 2006-03-28
forum: General Help
---

### Post by carlos1969 on 2006-03-28
Hi all, I was wondering if anyone could help me with the following issue.

I want to have to Linux OS's on my computer. I have selected Ubuntu and Linspire.

Here is what I did to set up my dual boot on a 40 G Hard Drive

I used System Commander to delete all partitions

I then installed Ubuntu (Breezy) on 20G of the HD. The rest was free space.

Once installed I used System Commander to format the free space as a Linux partition. I did this because the Linspire Install process would not see the free space.

Once I did that Linspire was able to see the partition and I installed Linspire on the second partition.

It seemed to have installed successfully and GRUB Loaded. I was able to see both OS's on GRUB

Linspire Loads but when I try to use Ubuntu I get Error 13

Invalid or unsupported executable format

Google says this about the error

This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

any suggestions?

---

### Post by carlos1969 on 2006-03-28
still here8)

---

### Post by r4ik on 2006-03-28
Have you read this one ?

[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

Might help.
Good luck !

---

### Post by carlos1969 on 2006-03-29
this problem is solved but I am not sure why the only thing I can guess is that linspire overwrote the GRUB

what happened

Installed Ubuntu
then Installed Linspire
GRUB Error 13


how it was solved, reversed the installations!

installed Linspire
then Installed Ubuntu

everything works great now!

---

