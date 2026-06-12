---
title: "Fat32 DST"
date: 2009-11-30
forum: General Help
---

### Post by soho on 2009-11-30
After a failed upgrade from 9.04 to 9.10 (my wifi didn't show up after upgrading) I reinstalled 9.10 (x64) from cd, but after reinstalling I have a problem with the file timestamps on my FAT32 external USB harddrive.
Before reinstalling all file timestamps matched those displayed if I boot in Windows, but after reinstalling one hour is added to all files in daylight savings time (DST) period of the year.
This gave me problems with my rsync based backup scripts, image exif timestamp mismatch and in general I would like my timestamps to be consistent regardless of booting platform.

How do I make Ubuntu compatible with the Windows interpretation of FAT32 timestamps of my removable media?

---

### Post by dcstar on 2009-12-01
> **soho said:**
> After a failed upgrade from 9.04 to 9.10 (my wifi didn't show up after upgrading) I reinstalled 9.10 (x64) from cd, but after reinstalling I have a problem with the file timestamps on my FAT32 external USB harddrive.
Before reinstalling all file timestamps matched those displayed if I boot in Windows, but after reinstalling one hour is added to all files in daylight savings time (DST) period of the year.
This gave me problems with my rsync based backup scripts, image exif timestamp mismatch and in general I would like my timestamps to be consistent regardless of booting platform.

How do I make Ubuntu compatible with the Windows interpretation of FAT32 timestamps of my removable media?

Set up both OSs correctly in the first place - all **actual** timestamps should be in Universal and not local time (as should all systems), and any **displayed** time should match the timezone set in the system.

---

### Post by dondos on 2009-12-14
This is my problem too. See [this thread]("http://ubuntuforums.org/showthread.php?t=961377"). I guess this is a bug on how the VFAT driver understands the timestamps of Microsoft's filesystems (FAT and NTFS). The only way to overcome this is to "lie" to both systems and configure them as GMT/UTC.

---

