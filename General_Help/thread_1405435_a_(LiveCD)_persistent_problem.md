---
title: "a (LiveCD) persistent problem"
date: 2010-02-12
forum: General Help
---

### Post by alienkid10 on 2010-02-12
I followed the tutorial here: [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) on LiveCD persistence using a casper-rw file at the root of a flash drive with a size of 512MB(tried 1GB samething). I booted into the CD and hit F6 added "persistent" and everything booted fine I install things etc. then reboot F6 "persistent" NOTHING! I loop mount the casper-rw file and find an empty folder called "lost+found" and nothing else. I am only booting from CD because many computers I use aren't able to boot USB.

---

### Post by alienkid10 on 2010-02-13
Bump

---

### Post by alienkid10 on 2010-02-13
BUMP I would like to get his working!

---

### Post by alienkid10 on 2010-02-17
BUMP!!!!!!!!!!!!!!!!!!!!!!!!!!

BUMP!!!!!!!!!!!!!!!!!!!!!!!!!!

IS this imposable?

---

### Post by efflandt on 2010-02-17
Have you tried using System > Administration > USB Startup Disk Creator (from any Ubuntu system or install CD if you have access to the iso you want to use from there)?  If you use the slider to set persistent data it it will automatically use it.  Persistent data is limited to 4 GB due to FAT32 file system limit, or on 4 GB or smaller flash, slider should be at least one click less that maximum.

You can add packages, but best not to try updates, because kernel is loaded from iso data before any persistent data is mounted.

---

### Post by alienkid10 on 2010-02-17
Yes I have booting from USB saves persistently to the USB but I can't boot USB on target computer(s) and would prefer not to mess with the BIOS on an aunt/uncle/school computer. That is why I am trying with a CD. Also booting USB customizing then booting CD with persistent does not load the casper-rw file at the root of the USB stick.

---

### Post by alienkid10 on 2010-02-26
BUMP still trying to get this working!

---

