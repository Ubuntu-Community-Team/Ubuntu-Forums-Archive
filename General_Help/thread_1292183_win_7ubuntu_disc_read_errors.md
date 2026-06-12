---
title: "win 7/ubuntu disc read errors"
date: 2009-10-15
forum: General Help
---

### Post by dreamweaverdreams on 2009-10-15
Hi I have been using ubuntu to put some files or a new ext HD. It's 1.5 tb partitioned by win 7 into 3. I have transferred quite a bit of data onto the first partition, a little on the 2nd partition and 3rd partition is empty. My problem is that win 7 won't read the first partition at all just says it needs formatting. it will read the 2nd and 3rd partitions. I've tried EXT2ifs which allows me to see all the partitions but when I try to access the 1st partition it just says it is corrupted and needs formatting. Can anyone help with this please?

---

### Post by Giblet5 on 2009-10-15
Open a terminal window.
Please post the output of this command ```
sudo fdisk -l
```

That will help us understand how the drive is currently partitioned.

---

### Post by louieb on 2009-10-15
I suspect the the 1st partition has an inode size of 256. the fsdriver only supports inode size of 128.

to check ( you will have to replace **/dev/sda1 **part of the example with the external partitions device name)

```
sudo tune2fs -l /dev/sda1 | grep Inode
```

---

### Post by dreamweaverdreams on 2009-10-15
This is the output from that command
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1136a2a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       59917   481177600    7  HPFS/NTFS
/dev/sda3           59918      121601   495476730    5  Extended
/dev/sda5           59918      119100   475387416   83  Linux
/dev/sda6          119101      121601    20089251   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf9b4fee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a0c3165

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       63742   512000000    7  HPFS/NTFS
/dev/sdc2           63742      127483   512000000    7  HPFS/NTFS
/dev/sdc3          127483      182402   441135104    7  HPFS/NTFS

---

### Post by dreamweaverdreams on 2009-10-15
> **louieb said:**
> I suspect the the 1st partition has an inode size of 256. the fsdriver only supports inode size of 128.

to check ( you will have to replace **/dev/sda1 **part of the example with the external partitions device name)

```
sudo tune2fs -l /dev/sda1 | grep Inode
```
Not sure if I got this right but this was the output from this command

tune2fs: Bad magic number in super-block while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.

---

### Post by Giblet5 on 2009-10-15
> **dreamweaverdreams said:**
> This is the output from that command

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a0c3165

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       63742   512000000    7  HPFS/NTFS
/dev/sdc2           63742      127483   512000000    7  HPFS/NTFS
/dev/sdc3          127483      182402   441135104    7  HPFS/NTFS

OK, so there are three NTFS partitions on the 1.5TB drive.

Was that your intention?

Are you certain that you formatted all three partitions?

It looks fine as far as partitioning.

---

### Post by dreamweaverdreams on 2009-10-15
> **Giblet5 said:**
> OK, so there are three NTFS partitions on the 1.5TB drive.

Was that your intention?

Are you certain that you formatted all three partitions?

It looks fine as far as partitioning.
Yes I formatted all three partitions with win 7. I was originally going to put all the files on this new disc from an existing ext drive using win 7 but it decided that it couldn't read that disc either and nearly wrecked it when it tried to do a chkdsk on it.

---

### Post by louieb on 2009-10-15
Sorry my mistake i saw >  I've tried EXT2ifs in your 1st post  a thought you had formatted the external drive with the ext2/ext3 file system.  

Read right past the part where you said you used Win 7 to format it. Can you still read / write to it with Linux? That would seem pretty odd if you can.

I think the same as Giblet5 - from a partitioning stand point it looks fine.

---

### Post by dreamweaverdreams on 2009-10-15
I can read and write to all my drives (inc the windows partition) with no problems from Linux. Even managed to get all the data back from the drive win 7 nearly destroyed. I would be more than happy to format the drives with a linux format if I could read it from win 7 but I'm afraid that I don't know how to do that yet.

---

### Post by Giblet5 on 2009-10-15
> **dreamweaverdreams said:**
> Yes I formatted all three partitions with win 7. I was originally going to put all the files on this new disc from an existing ext drive using win 7 but it decided that it couldn't read that disc either and nearly wrecked it when it tried to do a chkdsk on it.

OK, let's try a different angle. Why do you want three medium-sized NTFS partitions on the same drive v one big NTFS drive, or a big NTFS and a medium FAT32 drive?

Did you do anything tricky like tell Win7 that you want to mount one of these at a specific path eg, C:\Oracle?

/stumped

---

### Post by dreamweaverdreams on 2009-10-15
Thanks. This drive is purely for storing data which I will have to be able to access both on ubuntu and win7 on this computer and on my laptop. I'm paranoid about losing these files and unfortunately there is just too much to put on to dvd's. The first partition was for stuff that constantly changes, sometimes 10 - 20 times a day, the second partition is for stuff that I don't have to access very often and the third partition was for all the backups I do. I haven't done anything else with the drives except format them and put data on them and haven't told win7 to mount them at any particular path.

---

### Post by dreamweaverdreams on 2009-10-16
I've formatted a drive with exfat but Linux doesn't see it. I can't use fat because of the limit on the drive size. I've read on quite a few sites that Linux can write to NTFS, which it does seem to do, so why does Win 7 keep saying that the drive needs formatting? Why does Win 7 see the partition with only 150gb of data on it but not the partition with 400gb of data? Does Linux do something to the drive when a lot of data is transferred to it that makes windows think it's either unformatted or corrupt?

---

