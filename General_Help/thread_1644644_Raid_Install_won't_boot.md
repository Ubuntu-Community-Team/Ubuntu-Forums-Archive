---
title: "Raid Install won't boot"
date: 2010-12-13
forum: General Help
---

### Post by dsc3507 on 2010-12-13
Did a CD install, 64 bit Ubuntu 10.10 on Intel dx38 MB with Intel raid on two 160g drives.

I setup the raid drives (raid 1 mirrored) prior to installing. Install went without problems.  On reboot the volume will not boot.  I brought up again from CD and the volume is clean and mountable. There are two partitions - dm-1 and dm-2 swap

What can I do to make this boot?  

Doug

---

### Post by dsc3507 on 2010-12-13
OK solved my own problem. At least it boots now.

This was strictly  a Ubuntu installation, no other partitions, just the main partition and swap in dmraid raid1 volumes. What I did was determine the actual name of the partition - /dev/mapper/xxxxxxxxx and then I cd'ed to the root of the hard drive filesystem  and did:

fdisk /dev/mapper/xxxxxxxxx

once in fdisk I did a 'p' to view the partitions. There is a column for boot which is marked with an '*' if it is a boot partition. Mine had nothing marked as boot. I simply set the main partition as boot, saved the results, and rebooted and all was well.

If the install had done this I would not have had any problems.

---

