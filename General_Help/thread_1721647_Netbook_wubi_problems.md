---
title: "Netbook wubi problems"
date: 2011-04-04
forum: General Help
---

### Post by Tyler94 on 2011-04-04
About an hour ago, I used the wubi method of installing ubuntu 10.10 netbook edition. I burned the files to a Sony usb flash drive. Everything was smooth sailing until the installation was complete and it gave me the choice of booting into ubuntu or windows 7 starter, I naturally chose Ubuntu, than the very first choice after that. There was some white txt that said "No root device found" as well as some txt saying some things were missing. It then said something about busybox and told me to type "help" for existing commands.Can someone tell me what is going on and what do I need to do? My Netbook is an Aspire One D225. Thanks

---

### Post by Frogs Hair on 2011-04-04
This thread is a good resource for Wubi problems. [http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread](http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread)

---

### Post by Tyler94 on 2011-04-04
Here is what happens when I try to boot into ubuntu...
 
Gave up waiting for root device. Common problems:
- Boot args (cat/ proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat/ proc/ modules; ls/dev)
ALERT! /dev/sda3 does not exist. Dropping to a shell!
BusyBox v1.15.3 (Ubuntu 1:1.15.3- 1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
 
:confused:

---

