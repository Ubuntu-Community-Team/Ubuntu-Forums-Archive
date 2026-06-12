---
title: "Upgrading to RAID 1 - Trying to fix bootloader"
date: 2011-08-04
forum: General Help
---

### Post by Giraffro on 2011-08-04
I'm upgrading my PC by setting up a (fake) RAID 1 array. I've backed up my old hard drive using Clonezilla and tried restoring it while the array is active. However, I can't seem to fix the bootloader. The Ubuntu 11.04 LiveCD doesn't see the RAID array.

I have an ASUS M4A88T-M/USB3 motherboard that uses Advanced Micro Devices RAID option ROM utility to manage the array. Any suggestions?

---

### Post by dinu90 on 2011-08-04
Hi,

Are you sure the liveCD can see the RAID controller?

Try to open a console and run: lspci

Probably you need to load the drivers

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

