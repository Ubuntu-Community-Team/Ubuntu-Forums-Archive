---
title: "help with paritioning ubuntu"
date: 2011-11-03
forum: General Help
---

### Post by bradpurvis on 2011-11-03
My new pc came with a hard drive with raid set up on it. I've never partitioned ubuntu onto a raid drive before and I don't want to mess windows up. Can someone give me a basic walk through?

---

### Post by gsmanners on 2011-11-03
Here's a guide: (It's mostly on software RAID and LVM so I don't know if it really applies in your case.)

[https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html)

---

### Post by Mark Phelps on 2011-11-04
If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

