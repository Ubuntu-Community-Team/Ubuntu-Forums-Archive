---
title: "External HD does not mount after kernel update"
date: 2010-03-18
forum: General Help
---

### Post by 98cwitr on 2010-03-18
Ubuntu 9.10 on 2.6.31-20 kernel (updated today), using USB 2.5" enclosure w/ 80GB HD...flash drives mount fine. Drive has power to it via USB (confirmed). WTF is the problem here? command *sudo fdisk -l* does NOT list the drive. I use this drive for backups, so it's quite important to me. Any ideas?

---

### Post by Ozymandias_117 on 2010-03-18
does it show up in
```
sudo lsusb
```

---

### Post by 98cwitr on 2010-03-18
the bridge shows up...not the drive.  I can see it under Disk Utility, but when I try to format it as FAT32 I get this error:

> Error creating file system: helper exited with exit code 1: helper failed with:
mkfs.vfat: failed whilst writing FAT

BIG CORRECTION: It wasn't the update's fault...it was the damned G4L bullsh**t that corrupted my drive :mad:

---

