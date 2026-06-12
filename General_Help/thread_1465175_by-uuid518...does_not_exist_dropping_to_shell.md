---
title: "by-uuid/518...does not exist dropping to shell"
date: 2010-04-29
forum: General Help
---

### Post by madshad on 2010-04-29
I have no idea whats going on. i was using a program in wine. it basicly go stuck in a loop. so i just held the power button to reboot. 

after any restart i get the black screen,

gave up waiting for root device. common problems
-boot args (cat /proc/cmdline)
  -check rootdelay= (did the system wait long enough)
  -check root= (did the system wait for the right device)
-missing modules (cat /proc/modules; ls /dev)

alert! /dev/disk/by-uuid/51858d17-767e-4169...... does not exist dropping to a shell!!

---------------------
im busing ubuntu 9.10

---

