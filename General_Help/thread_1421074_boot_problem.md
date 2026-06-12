---
title: "boot problem"
date: 2010-03-03
forum: General Help
---

### Post by TroyStachnik on 2010-03-03
i just recently turned on my ubuntu machine and all i got was this window:

usplash: setting mode 1152x864 failed
usplash: using mode 1024x768
Gave up waiting for root device.  common problems:
-boot args (cat /proc/cmdline)
  -check rootdelay= (did the system wait long enough?)
  -check root= (did the system wait for the right device?)
-missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/1f1fcfbb-42c7-4ea2-b204-3896ec90cf04 does not exist. dropping to a shell!

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of built in commands.

(iniitramfs)

what does this meen?

---

### Post by quixote on 2010-03-04
It means that for some reason the machine is looking for ubuntu on the wrong partition.  Do you get a grub menu, and then the gobbledygook after it starts trying to boot, or do those messages happen before you see the grub menu?

Which version are you running: karmic, jaunty?

The important thing to remember is that everything is still there.  The boot process is pointing the wrong way, and that's not too hard to fix.  We need a few more details though, like the version, and also how many partitions you have and what OSes are on them.

---

