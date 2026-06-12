---
title: "Big Partition Table Problems - Please Help"
date: 2010-09-27
forum: General Help
---

### Post by RobstaHendricks on 2010-09-27
Hey guys,

Before I begin, may I add that I am new to the 'nux platform, other than a rather fancily skinned OS X.

So I have a problem with my partition tables where I am trying to resize my existing Fat32 partition to make room for an HFS+ partition. This is where, after a lot of trouble, I discovered using Parted Magic Live that the original Fat32 partition was actuall larger than the actual space available on the drive.

As you can see from GParted (images BeforePTChange.png and BeforePTChange2.png), the problem causes an error of "Can't have a partition outside the disk!".

[IMG]http://i1022.photobucket.com/albums/af344/RobstaHendricks/BeforePTChange1.png[/IMG]

[IMG]http://i1022.photobucket.com/albums/af344/RobstaHendricks/BeforePTChange2.png[/IMG]

So after a little more research, I found that there was a way to fix the partition table. The problem is that I didn't have any HD big enough to backup the data, and now neither Linux or OS X can find any viable partition.

So before I begin with the commands that I ran, below are the FDisk and SFDisk results prior to making any changes showing that the original Fat32 partition extended over the physical available space.

```
fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac255830

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   625153409   312576673+   c  W95 FAT32 (LBA)
```

```
sfdisk -d

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=       63, size=625153347, Id= c
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
```

I used the command below to adjust the partition to be within the available space:

```
echo "63,625137283,f" | sfdisk -f -uS /dev/sda -N2 -O sda_sectors_modified.save
```

```
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2            63 625142448  625142386   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2            63 625137345  625137283   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
Warning: partition 2 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)

```

This when poked with fdisk & sfdisk gave me the following repsones:

```
fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac255830

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   625137345   312568641+   f  W95 Ext'd (LBA)

```

```
sfdisk -d

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=       63, size=625137283, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
```


The problem is that now, GParted shows a logical partition, but no phsical partition within (AfterPTChange.png), which means that my data appears to have vanished, inclusive of important University files. I've also tried reverting to the original 'working' (but not resizable) partition table information, but neither one allows me to physically access my information.

[IMG]http://i1022.photobucket.com/albums/af344/RobstaHendricks/AfterPTChange.png[/IMG]

Here's hoping that one of you clever, clever people will be able to help.

Many thanx in advance.

Rob

---

### Post by bodhi.zazen on 2010-09-27
Try testdisk, it is in the repositories

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by RobstaHendricks on 2010-09-27
Thank you bodhi.zazen for making my content available again.

I still have the issue where I cannot resize the first partition to make way for a second though. Below are the fdisk and sfdisk outputs. Any further help to resize my partition to within the drive space available would be great.

[IMG]http://i1022.photobucket.com/albums/af344/RobstaHendricks/BeforePTChange1.png[/IMG]

```
fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac255830

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625153409   312576673+   c  W95 FAT32 (LBA)

```

```
sfdisk -d

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=625153347, Id= c, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

```

---

### Post by bodhi.zazen on 2010-09-27
If you can access the data I would back it up to an external media, wipe the drive, and re-partition it.

If you are still missing data, we can help with data recovery.

---

### Post by RobstaHendricks on 2010-09-27
Thanx again for the swift response.

The major issue is that I don't have enough available storage to back up everything, so ideally need to physically fix the partition until I can afford another external drive. This one is literally less than 2 months old, and served the purpose of moving files off of a smaller internal storage.

This poses a problem as I really need to repartition the drive to allow a couple of larger (6GB) files to be moved from the laptop itself. 

If any of you experts could help me to fix the extended partition issue, that would be great. I feel a lot more comfortable in the knowledge that we can always revert back to the starting point if necessary.

Thanx,

Rob

---

### Post by bodhi.zazen on 2010-09-27
Is it a FAT partition ? If that is the case you can try repairing the partition from Windows, the tools to fix FAT partitions are limited with Linux.

---

### Post by RobstaHendricks on 2010-09-27
Yea, it's a Fat32 partition, but the problem is that Partition Magic had the same problem as Parted Magic Live, but at least the latter gave me sufficient advice to attempt a fix.

Really need some advance advice, and from reading online, I have the right tool, but not sure that I correctly followed the instructions in the previous forum post I read ([http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)).

Regards,

Rob

---

### Post by srs5694 on 2010-09-27
First, keep in mind the distinction between a partition and a filesystem. (I have no reason to think that you don't understand this, but it's critically important, so I want to be sure you do understand it.) A partition is a contiguous set of sectors on a disk, identified by a disk partitioning system, such as the Master Boot Record (MBR) scheme that you're apparently using. A filesystem, OTOH, is a complex data structure that resides *inside* a partition or some other carrier (such as a floppy disk or a file). Typically, a filesystem is sized to exactly fill the partition in which it resides. It's possible to resize a partition without resizing a filesystem or vice-versa; but if the two aren't kept in sync, problems are likely to result.

Now, to your problem: Type "dosfsck -v /dev/sda1" and look for the line near the bottom of the output that identifies the total number of sectors in the filesystem, as in this example:

```

   6291456 sectors total

```

Now do some math: Call the value that's reported x. Add 62 to x. Let's call this value y. That's where the partition *should* end, if it's to be precisely the correct size for the filesystem it contains. Your disk size is 625,142,448. If y < 625,142,448, then something similar to your first solution attempt (using sfdisk) will work; however, you should change it so that you use the proper size and partition type code; so instead of

```

echo "63,625137283,f" | sfdisk -f -uS /dev/sda -N2 -O sda_sectors_modified.save

```

you'd use

```

echo "63,x,c" | sfdisk -f -uS /dev/sda -N2 -O sda_sectors_modified.save

```

Change 'x' in 'echo "63,x,c"' to the value for x that dosfsck reported; and note that you need to use 'c', not 'f', in that echo command -- that's why your partition became an extended partition originally. Alternatively, you can use fdisk to make these changes, but be sure to launch it with the "-u" option so you can work in sector units rather than cylinder units.

Backing up, if you compute y >= 625,142,448, then you're in trouble; the filesystem is too big for the disk. There may be a filesystem resizing utility that will cope with it despite this serious problem, but if so I don't know what program to recommend. If's conceivable that GParted or some other tool might deal with it if you resized the partition but not the filesystem, but I can't promise that, and it could even provoke another bug that might do more damage. IMHO, your best bet in this case is to do as bodhi.zazen suggests: Back up, wipe the drive, and create fresh partitions on it. I realize this may not be convenient, but it's better than risking your data by trying to force a utility to deal with the disk even though you know the disk is corrupt.

---

### Post by RobstaHendricks on 2010-09-28
Thanx for the detailed response, srs.

So I got at least a half successful result from the command 'dosfsck -v /dev/sda1'; x = 625142385. y = x + 62 = 625142447. And thus y < 625,142,448; the better result of the two circumstances detailed.

After this, I ran the command below:

```
echo "63,625142385,c" | sfdisk -f -uS /dev/sda -N2 -O sda_sectors_modified.save
```

Which before a reboot, strangely, displayed 2 partitions, SDA1 & SDA2, both labelled 'Robsta' (the correct partition name) in the file explorer.

[IMG]http://i1022.photobucket.com/albums/af344/RobstaHendricks/2Partitions.png[/IMG]

This was also backed up by the below FDisk & SFDisk command results, which seem to imply that the original partition still persists as well as the resized one:

```
fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac255830

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625153409   312576673+   c  W95 FAT32 (LBA)
/dev/sda2              63   625142447   312571192+   c  W95 FAT32 (LBA)
```

```
sfdisk -d

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=625153347, Id= c, bootable
/dev/sda2 : start=       63, size=625142385, Id= c
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
```

I'll give the machine a bounce, and state the results when it comes back up.

Thanx again,

Rob

---

### Post by RobstaHendricks on 2010-09-28
No joy,

As expected, a bounce brought back the same results as before. I have both the original partition (boot) which is too large for the drive's physical space, and the newly sized one; which fits perfectly both within the drive's boundaries, and to the outer limits of the file system contained within.

It looks as if we are now making progress, I suspect the problem though, is due to the fact that I used /dev/sda -**N2** instead of **N1**. This would mean that rather than modyfying SDA1, I added another partition within the physical disk boundaries of N1 as N2.

So basically, the first step is to non obtrusively remove SDA2's record, whilst persisting SDA1. Then finally, run the sfdisk command to actually change SDA1.

As I'm not entirely sure how to go about this, can anyone please tell me whether the command below would be correct?

```
echo "0,0,c" | sfdisk -f -uS /dev/sda -N2 -O sda_sectors_modified.save
```

In my mind, this would hopefully remove the instance of SDA2, ready to run the correct SDA1 command:

```
echo "63,625142385,c" | sfdisk -f -uS /dev/sda -N1 -O sda_sectors_modified.save
```

Can someone please specify if my assumptions are correct?

---

### Post by RobstaHendricks on 2010-09-28
So as per above, I need to know how to unobtrusively remove the erroneously created SDA2, which overlaps SDA1, then re run the command to set the boundaries of SDA1 correctly.

Anyone out there that knows how to achieve this?

---

### Post by srs5694 on 2010-09-28
Go into fdisk and delete /dev/sda1 by typing "d" and then "1" for the partition number. Then type "w" to save the partition table. The fact that the original partition will now be /dev/sda2 is unimportant.

---

### Post by RobstaHendricks on 2010-09-28
Thanx again, SRS, for all the help.

But I need a little clarification... I typed 'fdisk /dev/sda1' into terminal, then typed d, but got the following response:

```
fdisk /dev/sda1

Command (m for help): d
No partition is defined yet!
```

But when I do an fdisk -lu I got the following response, which shows that the partiton does exist:

```
fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac255830

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625153409   312576673+   c  W95 FAT32 (LBA)
/dev/sda2              63   625142447   312571192+   c  W95 FAT32 (LBA)

```

Am I using the fdisk command erroneously, as when I used fdisk alone, it simply listed the available params?

Many thanx in advance.

---

### Post by RobstaHendricks on 2010-09-28
Hi SRS,

I figured it out... Needed to do 'fdisk /dev/sda' rather than 'fdisk /dev/sda**1**'. For anyone reading in need of help, this fdisk's the entire drive, rather than the first partition. A further fdisk retrieved:

```
fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac255830

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2              63   625142447   312571192+   c  W95 FAT32 (LBA)
```

I'll bounce the box again, and see if this has made any difference to the partition tables in terms of GParted.

R,

---

### Post by bodhi.zazen on 2010-09-28
Please do not bump your own threads.

I believe you have twice been advised to back up your data and re-format.

You may also wish to try a windows forums as this is a FAT partition.

Otherwise you will need to wait until somebody with expertise looks on your thread.

---

### Post by RobstaHendricks on 2010-09-28
Hi bodhi.zazen,

Apologies for the bump.

I believe that I also replied twice stating that backup was not an available option, and the windows solutions did not work. 

As you can see from the latter posts, I am discussing this with a member with the expertise required, and now have a grasp of the tools which are being used.

The query itself seems open enough to apply to any form of Partition, and thus believe it to be correctly placed in a forum where, as such, Linux tools and commands are being.

R.

---

### Post by RobstaHendricks on 2010-09-28
Hi bodhi.zazen,

Apologies for the bump.

I believe that I also replied twice stating that backup was not an available option, and the windows solutions did not work. 

As you can see from the latter posts, I am discussing this with a member with the expertise required, and now have a grasp of the tools which are being used.

The query itself seems open enough to apply to any form of Partition, and thus believe it to be correctly placed in a forum where, as such, Linux tools and commands are being.

R.

---

