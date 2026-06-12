---
title: "select alternative kernel problem"
date: 2010-06-23
forum: General Help
---

### Post by yilin on 2010-06-23
If I select Ubuntu 10.04 LTS, kernel 2.6.31-21 Generic instead of
Ubuntu 10.04 LTS, kernel 2.6.31-22 Generic from booting memu, I got
this error:

mount: mounting none on /dev failed: No such device 6d966f507
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory

If I wait, it'll eventually boot into the system and everything seem ok.

Can anyone tell me how to solve this problem?


BACKGROUND:

My ubuntu 10.04 was upgraded all the way from 8.10 over the time. I can see the newer versions fix some problems and I'm fine until ubuntu 10.04 whith kernel 

Ubuntu 10.04 LTS, kernel 2.6.31-22 Generic

This makes my system very slow and unstable. I can tell how slow it is with dual core 2.2 Ghz (dell d630): the game Quadrapassel's one block drop from top to bottom took about 2 min !  Apps are randomly no responding etc...

By select older kernel seems solve the problem of slowness...

======================
I'm waiting for new updates and hope that'll solve current version's problem.

---

### Post by dcstar on 2010-06-24
> **yilin said:**
> 
........
My ubuntu 10.04 was upgraded all the way from 8.10 over the time.
........

Upgrading is always problematic with many issues like yours always appearing whereas fresh installs have far less of this sort of issue.

I would recommend you make a separate /home partition and then do a fresh install of 10.04.

---

