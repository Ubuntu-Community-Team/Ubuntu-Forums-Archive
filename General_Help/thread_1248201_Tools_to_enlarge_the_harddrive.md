---
title: "Tools to enlarge the harddrive"
date: 2009-08-23
forum: General Help
---

### Post by Go_Big_Blue on 2009-08-23
I have a 500GB HDD that I just used to recover a 160GB HDD using ddrescue (it's for my Windows XP machine).  When ddrescue finished, and I rebooted the computer, the HDD has 1 partition of 148GB and unallocated space of 317GB.  Are there any tools/programs on the LiveCD that I can use to increase the 148GB partition to say 310GB without losing any of the data?  I want to increase it because the partition indicates that it is 97% full.  This will give me additional space for the Windows XP installation, and I would still have sufficient enough space leftover to re-install Ubuntu 9.04 (approx. 150GB or so).

---

### Post by michy99 on 2009-08-23
Gparted is on the Live CD. Go to System->Administration->Partition Editor.

---

### Post by Go_Big_Blue on 2009-08-23
But by using Gparted and increasing the partition, will I lose all of the data?  Or will it just increase the size of the partition without affecting the current data that is there?

---

### Post by michy99 on 2009-08-23
It should not cause any problems, but it is always a good idea to backup data just in case the power goes out or something during the operation.

---

### Post by novafluxx on 2009-08-23
> **michy99 said:**
> it should not cause any problems, but it is always a good idea to backup data just in case the power goes out or something during the operation.

always have backups!! Always!!! Not just for special case scenarios!!! :p:p:p:p:p:p

---

### Post by Go_Big_Blue on 2009-08-23
Well ... given the fact that I just had ddrescue spend 51 hours reconstructing the contents of my old damaged hdd #-o believe me when I tell you that I have learned the hard lesson of always having backups. :biggrin:

Speaking of backups, what is the best/fastest freeware out there to do backups?  Any thoughts?

---

