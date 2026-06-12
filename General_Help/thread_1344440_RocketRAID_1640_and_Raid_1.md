---
title: "RocketRAID 1640 and Raid 1"
date: 2009-12-02
forum: General Help
---

### Post by diskmaster23 on 2009-12-02
I have decided to build a NAS server with the Highpoint RocketRAID 1640 in RAID 1, but I cannot seem to get the OS to recognize the array as a single drive, it keeps coming up as two separate drives.

Any advice?

*correction*
I cannot get ubuntu to bootup, the livecds go right into BusyBox, I don't have this problem if I take the RocketRaid out. I am going to try Suse and see what happens.

Although, if I use GPARTD, the clonezilla disc, it boots up, but see the raid as two drives and not one.

I originally wanted to setup this thing for Openfiler, but I am noticing this is a bigger issue than just problems with one flavor.

---

### Post by diskmaster23 on 2009-12-04
After messing around with Openfiler and Ubuntu, I just decided to use FreeNAS. It supported my RocketRaid 1640. The only thing that is doesn't work right yet is the CLI Raid Management Utility.

I suspect that the driver is outdated so I am going to update the drive by following the directions from [http://www.highpoint-tech.com/usa/bios_rr1640.htm](http://www.highpoint-tech.com/usa/bios_rr1640.htm)

Otherwise, FreeNAS 0.7 provided the proper driver support. This enabled me to use my RAID array. Even with Ubuntu 8.10, driver support for HPT374 is doesn't seem match FreeNAS's 0.7 capability. Perhaps it has something to do with the kernel modules or drivers, afterall, I am not the foremost expert at this stuff. I thank the *nix community for all their great documentation.

---

