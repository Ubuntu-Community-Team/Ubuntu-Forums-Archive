---
title: "Chkdsk vs. fsck.vfat"
date: 2012-03-27
forum: General Help
---

### Post by hallo200 on 2012-03-27
Hallo Forum,


I have a ubuntu server attached with a 2TB USB disk. It seems that there is a filesysetm Problem. I received an IO Error while doing the backup (rsync).

There is a vfat filesystem on it.

Is it better to connect the disk to a XP Machine and do chkdsk or is it better to do fsck.vfat to the disk?


ragards,
hallo200

---

### Post by oldfred on 2012-03-27
Does fsck.vfat still work? I thought that was obsoleted.

You just about have to use chkdsk from a Windows drive or Windows repairCD/USB. I have used a Windows 7 repairUSB to run chkdsk on my NTFS XP install.

If you have larger partitions you may want to backup & convert to ext4 partitions if not using any Windows. If using Windows NTFS is preferred over FAT as FAT has no journal and cannot store files over 4GB.

---

### Post by mastablasta on 2012-03-27
not sure about that error, but when widnows XP was acting up on the wd green disk (simply didn't want to have a stable boot) i booted with USB linux and it immediatelly/automaticly repaired the disk. gave up on the disk with NTFS, now testing EXT4 on it and data only. no errors yet, so far...

---

