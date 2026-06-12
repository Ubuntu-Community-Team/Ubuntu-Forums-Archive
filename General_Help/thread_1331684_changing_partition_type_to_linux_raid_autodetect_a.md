---
title: "changing partition type to linux raid autodetect after array already running"
date: 2009-11-19
forum: General Help
---

### Post by stuyguy on 2009-11-19
Hi,

    I recently suffered two failures to my RAID-5 mdadm array due to bad disks and have recovered everything successfully (one disk died at a time).  Unfortunately, each time I put in the replacement drive, I partitioned them as Id=83 "Linux" instead of as Id=fd "Linux raid autodetect".  As a result, I have the following:

/dev/sdb1 and /dev/sde1: Id=83
/dev/sdc1 /dev/sdd1, /dev/sdf1, (...): Id=fd

My question is, can I change the partition table type on a live array?  Or would I have to take a disk down, repartition, and re-add it to the array and go through the whole rebuild process?

Thanks.

---

