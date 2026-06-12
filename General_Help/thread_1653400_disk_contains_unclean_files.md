---
title: "disk contains unclean files?"
date: 2010-12-26
forum: General Help
---

### Post by ohVaNiLLaGoRiLLa on 2010-12-26
I have never used ubuntu before and I installed it via wubi to I could try it out. After I installed it and rebooted it worked just fine. Then I shut it down and come back later to discover this when I boot my computer back up after choosing ubuntu. 

[http://img87.imageshack.us/img87/9119/photo3ro.jpg](http://img87.imageshack.us/img87/9119/photo3ro.jpg)

what...

and the operating system i have installed in Windows XP pro and i used the ubuntu-10.10-desktop-i386.iso

---

### Post by WorMzy on 2010-12-26
Hmm, at a guess, chkdisk (the windows disk checker) moved root.disk to a recovery folder under C:\. This is one of the problems with Wubi installations. You'll need to move the root.disk back to C:\Ubuntu\disks\ before you can boot to Ubuntu again.

A better solution would be to install Ubuntu to it's own partition.

---

### Post by ohVaNiLLaGoRiLLa on 2010-12-26
alright thanks. I know I should partition it but I wanted to try it out first.  I was really looking for a way to boot ubuntu off of a usb stick when i found wubi.

edit:
i just checked that out and it appears that under C:\ubuntu\disks that root.disk is still there.. where is it suppose to be?

---

### Post by ohVaNiLLaGoRiLLa on 2010-12-27
bump

---

### Post by bcbc on 2010-12-27
Boot from a live CD, mount your windows partition and run fsck on the root.disk.

If you need help with this, please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Otherwise, the instructions are in the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?"). (Note, don't run fsck on a mounted file system - so don't loop mount and then run fsck on the root.disk - the wubi guide is a little unclear as it seems like the fsck follows the mount)

---

