---
title: "NTFS partition recovery"
date: 2010-08-23
forum: General Help
---

### Post by Nordvind on 2010-08-23
Was moving some files from ext4 partition to NTFS one, and PC got hanged. After reboot, partition refused to mount, GParted showing "Error (5): opening dev/dsa2 as NTFS failed: Input/output error". GParted also suggests me to run *chkdsk* on Windows to fix this. Problem is, I got no Windows installed :mad:

Could you please suggest similar Ubuntu programs, for NTFS recovery?

P.S. Tried *ntfsfix*, it says volume is corrupt, and again advices using that *chkdsk*.

---

### Post by LowSky on 2010-08-23
Sorry but I don't think there really is a Linux option for checking NTFS partions that beocme corrupted. You will need a computer with Windows to repair it. If anything ask a friend to help you out.

---

### Post by Nordvind on 2010-08-23
Solved the problem, by connecting a second HDD with Windows onboard, and disk-checking the 'corrupted' partion. ;)

Anyway, I can't believe there are no utilities for recovering NTFS under Linux. I've googled up a couple of, that are claimed to help - *testdisk*, for example. Will try them out next time.

---

### Post by Charlietje on 2010-08-23
maybe you should keep a bartpe cd if you still having ntfs disks

---

### Post by srs5694 on 2010-08-23
NTFS is proprietary and undocumented. That's why it's taken so long (over a decade) for Linux NTFS support to reach the point that it has. I wouldn't expect Linux-native NTFS repair utilities to appear any time soon, although of course it could be that something's in the works and I don't know about it.

In the meantime, if the system doesn't run Windows at all, I strongly recommend you migrate to a Linux-native filesystem ASAP. You've discovered one good reason for this: A system crash or other filesystem error makes your NTFS partition(s) unusable until you can check it with Windows, which will be, at best, a nuisance. Another reason is that Linux filesystems provide better support for Linux-native filesystem features, such as ownership and permissions. There may also be performance issues, although I don't know how much of a performance difference there is between NTFS and various Linux-native filesystems. Ubuntu implements NTFS via a user-space driver, which means it's handicapped compared to the in-kernel drivers that are used for Linux-native filesystems.

Of course, if you've got a huge amount of data on NTFS, migrating to a Linux-native filesystem might not be convenient or easy. If you've got to put it off for a while because of this, then so be it. You should definitely keep this in mind for next time it's practical, though, such as when you upgrade your hard disk or re-install Linux.

---

