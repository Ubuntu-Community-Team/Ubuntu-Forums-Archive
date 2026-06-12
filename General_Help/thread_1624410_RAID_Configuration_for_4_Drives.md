---
title: "RAID Configuration for 4 Drives"
date: 2010-11-17
forum: General Help
---

### Post by spl3001 on 2010-11-17
I am currently setting up a server at work.  It will almost certainly be used only as a file server.  Since I have a little latitude about how to go about this, I decided to build a computer from scratch and use four 1TB hard drives.

Basically the setup I would like to have is the following:
2 drives used as a global any-one-can-read-and-write space (offering 2 TB)
2 drives that back up the first 2 drives.

It occurred to me that it would have probably been easier to have 5 drives (1 for OS, 2 for storage, 2 for backup), which I may end up doing, assuming I have at least one more SATA connector on the motherboard.

Would using RAID be an option?  It seems like I would need a mix of two different RAID systems.  Speed isn't really an issue, we only have about a dozen people in the office and no more than 2 or 3 would be accessing at any one time.

I am using Ubuntu 10.10 Desktop edition (Server seemed a bit too much for what I wanted to do).

---

### Post by BobMUK on 2010-11-18
Consider using all 4 (or 5) drives as a RAID 5 array under mdraid, then putting LVM on top of the array to produce "partitions" of whatever size you require.

This will allow any single disk to fail without losing an of your data.
> Basically the setup I would like to have is the following:
2 drives used as a global any-one-can-read-and-write space (offering 2 TB)
2 drives that back up the first 2 drives.

You then won't need the 2 backup drives as you'll already be fault tollerant.

---

