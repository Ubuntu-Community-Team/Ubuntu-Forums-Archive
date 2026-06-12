---
title: "Cannot get Storage Device Manager (pysdm) to show partitions"
date: 2009-12-05
forum: General Help
---

### Post by Ken Cameron on 2009-12-05
I cannot seem to get Storage Device Manager (pysdm) to show the partitions on my hard drive although I can access these without trouble from Places.
 

 The details of my drives are:
      Device Boot      Start         End          Blocks   Id  System 
     /dev/sda1   *               1       22241   178650801    7  HPFS/NTFS 
     /dev/sda2               23592       24321     5863725    c  W95 FAT32 (LBA) 
     /dev/sda3               23336       23591     2056320   82  Linux swap / Solaris 
     /dev/sda4               22242       23335     8787555   83  Linux 
 


 sda1 is my Windows XP partition and sda2 is a backup one.   The others are self explanatory.   I have just upgraded to Ubuntu 9.10 with Grub 2.   The same setup on my laptop works fine.
 

 In order to easily have access to files in the Windows partition I would like to automount sda1 when Ubuntu starts.  Whin I start SDM (pysdm), although sda is shown, the arrow to expand the partitions is missing and the rest is greyed out!


  Any ideas how to sort this?   I have tried deleting and re-installing pysdm without success.

---

### Post by Ken Cameron on 2009-12-07
Solved this problem of automounting the drive by using the ntfs-config utility.   Still cannot, however, get Storage Device Manager (pysdm) to show the drive partitions!

Would still like an answer to this if anyone has it.

---

