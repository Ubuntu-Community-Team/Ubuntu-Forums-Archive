---
title: "Windows recovery manager"
date: 2010-08-03
forum: General Help
---

### Post by alexpwnsn00b2 on 2010-08-03
ok well school is about to start and i found out i need to install a  program that only works on a windows computer so i now need to install  vista basic again. the netbook is currently using ubuntu 10 i kept the  recovery partition intact just in case something like this came up. when  i go into the recovery manager i click the restore computer to factory  settings, but when i proceed with the process i get a message box that  says "One of the service DiskPart uses returned a failure .ErrorCode=0,  the operation completed successfully." then when i click ok the computer  reboots but nothing happened. any thoughts?

---

### Post by alexpwnsn00b2 on 2010-08-03
Could the problem be that the recovery manager is looking for the C drive and none of my partitions have a letter? How would you give a partition a letter using ubuntu?

---

### Post by sikander3786 on 2010-08-03
> **alexpwnsn00b2 said:**
> Could the problem be that the recovery manager is looking for the C drive and none of my partitions have a letter? How would you give a partition a letter using ubuntu?

Hi.

You can't give names like C: to partitions in Ubuntu. Here the name structure is different. Still when you boot Windows CD on Ubuntu machine, it returns the first volume as C: second D: and so on. Mean Ubuntu has nothing to do with it.

I don't think it is a problem due to the naming structure. Still you can use any of the proprietary or even free NTFS/FAT partition manager to restore the partitions and see what happens.

Regards.

---

