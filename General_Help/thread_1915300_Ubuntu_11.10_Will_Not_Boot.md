---
title: "Ubuntu 11.10 Will Not Boot"
date: 2012-01-25
forum: General Help
---

### Post by JDog2pt0 on 2012-01-25
So Ubuntu will not boot. After the splash screen, an error appears and a few more lines show up, acts like it's going to boot, but it doesn't. Here's the error: ```
FATAL: Error inserting vesafb (/lib/modules/3.0.0-14-generic/kernel/drivers/video/vesafb.ko): No such device
```I've been using Ubuntu live on a flash drive, and Chroot to access my drive and test a few different things. I've seen the error in the past, but it only did this after I removed a bunch of Unity stuff (I use Cinnamon and left Gnome 3). vesafb is not blacklisted.

Note: I've been setting up Chroot so I can launch applications from my disk, mainly Synaptic package.

---

### Post by JDog2pt0 on 2012-01-26
Solved it, had nothing to do with vesafb. Accidentally removed Unity-Greeter so I had no login interface.

---

### Post by arunharidas on 2012-01-26
then mark the thread as solved buddy :D

---

### Post by nipunshakya on 2012-01-26
:d

---

