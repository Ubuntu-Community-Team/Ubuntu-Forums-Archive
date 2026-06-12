---
title: "Setting up exisintg RAID1 on new install"
date: 2009-12-01
forum: General Help
---

### Post by skunkfifty on 2009-12-01
Hey, I decided to reinstall 9.10 from scratch after the upgrade failed miserably (system was wildly unstable). On this machine I have the OS installed to a separate drive and 2 1TB drives setup as a RAID1 for data storage. 

The installer let me setup the RAID but like a genius I forgot to assign them a mount point at that time. After everything was backup, I tried to mount /dev/md0 but it gave me errors, upon researching it I found /dev/md0 did not have a partition table.

My gut told me that giving /dev/md0 one would destroy the data already on the disks. Which would not be very fun.

So my questions are:
Am I correct in thinking that if i give md0 a partition table that the data already on the 2 drives will be lost?

And if so Where do I go from here?

---

