---
title: "slow startup"
date: 2010-05-01
forum: General Help
---

### Post by Speed Of Light on 2010-05-01
[SIZE="2"]Hi
I'm using the new Ubuntu 10.04 (amd64), I installed lots of software from the software center and it is still very fast!
but on startup it hangs for about 25 seconds without any HDD activity, I can only see a black screen and my cursor!
I tried removing everything from "System > Preferences > Startup Applications" ... but no significant change.
I think this "hanging" occurs before login, because when I logout I can login again very fast.

Any Ideas/Help ?[/SIZE]

---

### Post by Owen.C93 on 2010-05-01
> **Speed Of Light said:**
> [SIZE=2]Hi
I'm using the new Ubuntu 10.04 (amd64), I installed lots of software from the software center and it is still very fast!
but on startup it hangs for about 25 seconds without any HDD activity, I can only see a black screen and my cursor!
I tried removing everything from "System > Preferences > Startup Applications" ... but no significant change.
I think this "hanging" occurs before login, because when I logout I can login again very fast.

Any Ideas/Help ?[/SIZE]
Enable automatic login and see what that does. Are you using preload?

---

### Post by Speed Of Light on 2010-05-02
Automatic login is already enabled.
and no I'm not using preload

---

### Post by dino99 on 2010-05-02
" I installed lots of software from the software center "

so how about free space into the different partitions ?

sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

### Post by Speed Of Light on 2010-05-02
I have enough free space in all partitions, and I tried your advice ... but it didn't fix it
I also tried reinstalling gdm and plymouth packages from synaptic, not only it didn't help, but it made some side effects:
- "gdmsetup" now doesn't "unlock"!
- Compiz effects are not being applied.

I tried reinstalling gdmsetup and compiz packages from synaptic.
but it didn't help.

my problems are growing just like a snow ball !
Please help me before I break the system, and reinstall it back again.

---

### Post by Speed Of Light on 2010-05-02
> so how about free space into the different partitions ?
I got a sudden message telling me "low disk space" !
but in "system monitor" File Systems tab it says that only 14% of the system drive is full !
anyway, I did free some space, but no change.

I'm confused O_O

---

### Post by Speed Of Light on 2010-05-07
Okay, I've reinstalled Ubuntu, and I'm still having the same problem (the system hangs for about 25 sec at startup)!

Here are some additional info:
- This "hanging" still exist even **before any software installation**.
- When I disabled automatic login, I find that this "hanging" occurs **after I press login button**.
- There are no side effects to this problem, I mean every thing else is like charm !

---

