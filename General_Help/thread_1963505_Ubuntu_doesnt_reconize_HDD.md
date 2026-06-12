---
title: "Ubuntu doesnt reconize HDD"
date: 2012-04-22
forum: General Help
---

### Post by dim505 on 2012-04-22
I installed ubuntu for the first time today though a flash drive on my sdd. It saw my hdd when i installed it on my sdd but now when i boot up i cant see my hdd, its a internal hdd not a exrteral and i have ahci mode enabled in the bios. Any suggestions will be appreciated

---

### Post by efflandt on 2012-04-22
What type of partitioning does the drive have, msdos partitions or something else?

Post the output of **sudo fdisk -l** (small L) and wrap it in code tags by highlighting that and clicking **#** in message window.

I am running 64-bit 11.10 on SSD (sdb) and boot everything from its grub in mbr of that drive.  But that and sda have msdos partitions, so it has no trouble mounting ntfs or Linux partitions on sda using the file manager (sdb only has the 11.10 partition).  I don't use any swap (8 GB RAM).

---

