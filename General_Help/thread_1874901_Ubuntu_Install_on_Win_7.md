---
title: "Ubuntu Install on Win 7"
date: 2011-11-04
forum: General Help
---

### Post by Zishenkao on 2011-11-04
Hey I'm trying to install ubuntu I tried to do it once, it failed so i uninstalled and tried again, but when i try to reinstall it says Previous instillation detected and Exits. Any Ideas

---

### Post by community on 2011-11-04
Whether you installed it on HDD or was it a wubi install?

---

### Post by just_abhi22 on 2011-11-04
why dont you format the partition on to which you had previously installed UBUNTU via UBUNTU or using WIN 7 CD.start the thing fresh....

---

### Post by Mark Phelps on 2011-11-04
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

