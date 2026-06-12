---
title: "RAID Drive Error Xubuntu 10.04 on Boot"
date: 2010-05-02
forum: General Help
---

### Post by jeffers.r on 2010-05-02
I'm running an Intel x86 machine with 4 hard drives, as follows:

sda - Ext3/Swap, Xubuntu 10.04
sdb - NTFS Drive, Vista
sdc - NTFS, Disk 1 of Intel RAID1, labeled "Data"
sdd - NTFS, Disk 2 of Intel RAID1, labeled "Data"

I just performed a clean installation of Xubuntu 10.04 on sda using the Alternate CD in order to support the RAID drives. Installation went fine, and the RAID drives are listed within /dev/mapper as isw_ciggeaiihd_Data1, which I've mounted and can access without any issues.

Upon the first restart (and all subsequent restarts) after the installation, I am presented with the following errors immediately after the GRUB screen during boot:

```
udevd-work[##]: inotify_add_watch(6, /dev/sdc, 10) failed: no such file or directory
udevd-work[##]: inotify_add_watch(6, /dev/sdd, 10) failed: no such file or directory
```At this point, the boot hangs for 15 seconds or so, and then continues to load  normally (or at least appears to). The drives identified are the two drives for the RAID1 setup, so my questions would be:

a) should I be concerned that the raid isn't working properly, and;
b) is there a way to remove the errors to reduce the boot time (and clean it up)?

I previously had Xubuntu 9.04 installed (also with the Alternate CD and RAID controllers) and never had any issues or errors on boot.

Many thanks for your thoughts!

UPDATE: might be related to this bug #[568050]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/568050").

---

### Post by frank_claessen on 2010-05-17
Hi there,

I have a similar problem, although not with RAID but with a logical volume. The drives being used as physical volumes are the ones referred to in the inotify_add_watch error.

Think this is a bug indeed.

Cheers Frank

---

### Post by martyz1 on 2010-09-01
udevd-work(94)inotify_add_watch(6, /dev/sdd,10)failed: no such file or directory
                 93
                 95
What version of Cryptsetup and how is it installed?  Ubuntu fails to start after this msg.  I had Raid once opon a time...Installed to one of the 3 disks.:(
Thanks for any imput:KS,
Martin

---

