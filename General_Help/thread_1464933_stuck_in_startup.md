---
title: "stuck in startup"
date: 2010-04-28
forum: General Help
---

### Post by gold dust gospel on 2010-04-28
ok. 

I am an absolute beginner and confused by the jargon, but here's my problem...
I've been stuck in startup for two months and have tried much of the advice found on the forums but still no luck! I have a live disc but I REALLY need to recover files from my existing (but inoperable) system! Someone please help!

this is exactly what the screen says upon startup...

-Boot args (cat /proc/cmd line)
      -Check rootdelay= (did the system wait long enough?)
      -Check root= (did the system wait for the right device?)
Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/8b3856ab- b852-4c7c-8578-1465d33a5f77 does not exist. Dr
opping to a shell!

BusyBox v1.33.3 (ubuntu 1:1.13.3-1ubuntu7) built-inshell (ash)
Enter 'help' for a list of built -in commands.
(initramfs)
(initramfs)

---

### Post by kbielefe on 2010-04-28
At this point, it is probably easiest to boot to the live CD, mount your hard drive to copy whatever you need off of it, then reinstall ubuntu.  Some instructions for doing that are [here]("http://ubuntuforums.org/archive/index.php/t-316580.html").

---

