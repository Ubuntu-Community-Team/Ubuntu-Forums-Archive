---
title: "Ubuntu or Hardware problem?"
date: 2009-12-14
forum: General Help
---

### Post by novice1969 on 2009-12-14
My machine shut down and when I rebooted I got the following:

Screen init failed

Gave up waiting for root device. common problems:
-Boot args (cat/proc/cmdline)
-check rootdelays = (did the system wait long enough?)
-check root (did the system wait for the right device?)

missing modules (cat/proc/modules) ls/dev


ALERT! /dev/disk/by-uuid/ade5eaa2-2aba-4d7a does not exist
Dropping to a shell!

BusyBox v1.13.3 (ubuntu 1:1.13.3-1 ubuntu7) built in shell

Extra 'help' for a list of built in commands.


I did a self check on the hard drive and it came back as fine. What else could I do to get this machine to boot up?

---

### Post by varangian on 2009-12-14
Perhaps a good first step would be to try booting from the install CD/Flash drive from which you installed originally. If that all works then you'll at least know the basic h/w is working OK. If so then there may well be a problem with the drive that hasn't been detected. Open a terminal and try:

sudo fdisk -l

and see if that finds your boot drive or not. The thread [_here_]("http://ubuntuforums.org/showthread.php?t=433710") has more details on what you could try from then on.

---

