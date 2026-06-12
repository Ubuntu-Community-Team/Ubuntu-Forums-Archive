---
title: "Lost Backup Data"
date: 2011-07-16
forum: General Help
---

### Post by JBA2337 on 2011-07-16
I have two hard drives in my computer. The primary one is used to dual-boot Ubuntu and Windows XP. The second drive, 60 GB (NTFS) is only used for backups. I have no idea how this happened, but somehow the backup drive lost all its data. The only thing that shows on that drive are the directories: RECYCLER and System Volume Information.

I ran Testdisk and selected the 60 GB drive. The screen shows:

```
Disk /dev/sdb - 60 GB / 55 GiB - CHS 7297 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS              0   1  1  7296 254 63  117226242 [DriveEntfs]
No partition is bootable
```

After I did a deep search, no other partitions were found. The screen shows the same information as above, except that to the left of "HPFS - NTFS" there is an * instead of a P. That is strange, because this drive is not bootable. In Testdisk if I go to Advanced>Boot, and if I select "Repair MFT", I get a message:
"MFT and MFT Mirror are bad. Failed to repair them." 

I know that my data is still on this drive, because in Windows I ran the program "Recuva", and it did recover most of the files that I had saved from Windows and from Ubuntu. Recuva can recover files, but they are not arranged in a very usable way. The original directories in which the files were located are not recovered. So I have about 4000 files, but there is no way to easily put them back where they belong.

Does anybody have an idea how I can recover or repair the MFT on this drive?

Is there any other software that you could recommend, that would recover the lost files and arrange them in the proper directories?

Thank you.

JBA2337

---

