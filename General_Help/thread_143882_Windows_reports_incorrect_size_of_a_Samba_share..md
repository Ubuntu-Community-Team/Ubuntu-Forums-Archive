---
title: "Windows reports incorrect size of a Samba share."
date: 2006-03-13
forum: General Help
---

### Post by mobilegod on 2006-03-13
I've added a 60GB drive to be used as a samba share for the rest of my network. I partitioned it to have one partition using the whole space on the entire drive.  After partitioning fdisk reports the following:
___________________________________
Disk /dev/hdd: 60.0 GB, 60000000000 bytes
16 heads, 63 sectors/track, 116257 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1      116257    58593496+  83  Linux

___________________________________

When I restart Samba and connect to the share from a Windows box it reports the size as 23.0GB

Does anyone have any idea what's going on here?

---

