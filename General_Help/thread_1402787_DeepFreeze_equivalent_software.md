---
title: "DeepFreeze equivalent software"
date: 2010-02-09
forum: General Help
---

### Post by conradin on 2010-02-09
Hi all,
I have a program called Deep Freeze 5 produced by farconics that saves the state of my Microsoft Windows computers such that when the computer reboots, the original set up (at time of freeze) returns on the next boot. I want to setup Ubuntu on several of the computer labs in my department, but I don't want to have to tinker with the setups repetitiously. 

If anyone out there is familiar with the product DeepFreeze, can someone point me to a similar software package for ubuntu?

---

### Post by patchwork on 2010-02-09
Although I'm not familiar with deepfreeze, here is a thread that seems to tackle the same issue.  

[http://ubuntuforums.org/showthread.php?t=1130779](http://ubuntuforums.org/showthread.php?t=1130779)

The Live CD iso image is an interesting idea...

---

### Post by rahilm on 2010-02-09
there is something called guest session in ubuntu...you might want to try that out

---

### Post by cdenley on 2010-02-09
I've mounted the root filesystem with aufs before, which basically turns your hard drive install into a livecd. Users with root access can remount the root filesystem, though. A solution I liked much more was to simply use tmpfs for a user's home directory, since non-admin users couldn't modify anything else anyway. Admin users (yourself) can still make changes as usual. I believe this is how the "guest session" works.

---

