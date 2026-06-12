---
title: "Kernel writing to disks preventing spindown"
date: 2011-02-15
forum: General Help
---

### Post by m00dawg on 2011-02-15
Recently I have noticed that my home NAS is not spinning drives down like it used to and I suspect it may have to do with upgrading from 9.04 to 10.10.

For some reason, even if I unmount my file-systems on said disks and stop all the processes I can think of (save for SSH), I am still seeing occasional disk writes. It's teeny tiny data and happens about once every few minutes.

I suspect it has something to do with MD, LVM, or XFS as I am using all of those on-top of the physical drives. MD is setup with a RAID1 on two matching SATA drives, LVM then carves that up and XFS sits on the results. Previously, I didn't have any issues with drive spin-down so I know something must have changed.

Any thoughts on how to find out what is writing to the disk? 'lsof' doesn't show much and, since it may be a kernel driver doing it, I'm not sure it would be of much use there?

The OS is running off a CompactFlash card (with a plethora of tmpfs partitions for things that do write often to avoid wear) with /home really being the only thing mounted on the spinning media.

I noticed that the anticipatory scheduler is no longer available after upgrading my kernel so I suspect that might have something to do with it.

---

