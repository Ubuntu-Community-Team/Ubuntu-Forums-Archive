---
title: "Need help mounting CF card in PCMIA adapter"
date: 2006-04-26
forum: General Help
---

### Post by tsb on 2006-04-26
I can't get it recognized.  When I hover over the card in storage media it says "Device Node:  /dev/hde1"

I tried to add a line to fstab "/dev/hde1       /media/hde1     vfat    rw,user,noauto  0       0"

When I try to mount the card in storage media it says "mount: mount point /media/hde1 does not exist
Please check that the disk is entered correctly."

How do I get it to work?

thanks

---

### Post by tsb on 2006-04-26
nevermind sudo mkdir /media/hde1 solved the issue

---

