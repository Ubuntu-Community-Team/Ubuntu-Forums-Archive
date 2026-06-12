---
title: "ssd disk problem"
date: 2011-11-08
forum: General Help
---

### Post by Ofloo on 2011-11-08
hi,

I have this strange problem with my acer aspire one ssd disk, when i noticed ubuntu wouldn't load anymore i figured i'd reinstall, this time was going to use xubuntu cause of the unity desktop which seems to require a lot of resources, .. but when i wanted to partitionate the disk i get a lot of read/write errors, .. even dd if=/dev/zero of=/dev/sda bs=8192 count=8192 will not work then however when i get my freebsd livefs usb stick i am able to null the drives, create partition table, however one of the drives i'm not able to create newfs, .. get some error about zero length, .. i figur one something is wrong with one of the sectors on the disk, .. 

My question is there a way to fix this problem? or is there an howto how to diagnose this, .. so i know for sure the disk is broken? Because on linux the entire ata driver crashes, and after that the disk isn't visible anymore in gparted, when attempting to create new file systems.

oh i also get some superblock errors, .. that there not readable?

---

