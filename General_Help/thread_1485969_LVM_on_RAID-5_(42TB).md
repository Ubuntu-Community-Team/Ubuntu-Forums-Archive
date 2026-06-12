---
title: "LVM on RAID-5 (4*2TB)"
date: 2010-05-17
forum: General Help
---

### Post by stek_87 on 2010-05-17
Hi!

I'm running an Ubuntu server 9.10 and would like to start using LVM.

I have set it up with 3 raid volumes.

One 4-disk raid-1 10GB for /
One 4-disk raid-1 1GB for swap
And one 4-disk raid-5 ~6TB as datastore for vmware esxi.

The raid-5 voluime is divided in to two partitions, one 2TB ext3 and one 4TB XFS.

Now I would like to try using LVM for the 4TB volume, so that I can use the snapshot function and backup my vm files within the datastore.

Does any one know if it is possible to do so, just for a partition of a drive or do I also have to destroy the 2TB ext3 volume to do this?:-k

If possible, can anyone point me to right direction?

rgds

---

