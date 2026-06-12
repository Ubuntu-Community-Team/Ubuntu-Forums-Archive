---
title: "Files lost during copy from EXT3 to FAT32 no errors reported?!"
date: 2010-03-01
forum: General Help
---

### Post by jarthurs on 2010-03-01
I've just copied 130Gb of files from my old Ubuntu (9.04) machine to a 160Gb FAT32 removable drive, took a few hours to complete. Having checked the source and destination folders, all the files are missing!

I've connected the FAT32 drive to a different (XP) machine and could then see about 20Gb of files, tried running undelete on the drive but there is nothing present except the 20Gb of visible files.

Nothing in the trash folders on the removable drive or the host machine and I can't locate any of the files on either drive (aside from the 20Gb that are visible).

WTF!?

I lost 500Gb of data to a faulty drive a few months back, so backed up the remaining data to various drives (including this removable one) and have been gradually copying it all back to a newly installed RAID5 NAS box. Now I've lost another 110Gb to some sort of rogue copy failure.

Anyone come across this before?

ARGH!

J.

---

### Post by jarthurs on 2010-03-01
Looks like it failed to unmount properly and the FAT was corrupted. Managed to repair the FAT and as far as I can recall all the files have reappeared.

Phew!

J.

---

### Post by oldfred on 2010-03-01
FAT is not the best file system to use unless you absolutely have to for cameras or other devices. For compatability with windows NTFS is better as it at least has some recovery capability. You also cannot copy files over 4GB (less one byte).

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

