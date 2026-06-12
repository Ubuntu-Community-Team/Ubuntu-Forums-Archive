---
title: "Installing ubuntu server alongside windows 7"
date: 2011-09-28
forum: General Help
---

### Post by XquisiteBee on 2011-09-28
Hi,

I would like to setup a dual boot of Ubuntu Enterprise Cloud alongside Windows 7, is that possible?  I tried doing so but got a message stating that I did not specify any partition.

Any assistance would be greatly appreciated.

---

### Post by Mark Phelps on 2011-09-28
Given the ease with which Win7 installs can be corrupted, it would be very helpful if you had a Win7 Repair CD around.

You can do that by launching the Backup feature and choosing the option of making a Repair CD.

Also, don't allow any Linux installer to shrink your Win7 OS partition; instead, go into Win7 Disk Management and shrink the partition yourself.  While you're there, look at your partitions. If you already have four, do NOT, repeate NOT, use the option to create any more of them.  You will have to REMOVE one of the partitions to install Ubuntu as four is the maximum number of Primary partitions allowed.

If you have less than four partitions, then go ahead and use the Disk Management utility to shrink one to make room.

But after you do that, and BEFORE you do the Ubuntu install, create the Win7 Repair CD.

---

