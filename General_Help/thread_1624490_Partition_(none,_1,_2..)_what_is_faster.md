---
title: "Partition (none, 1, 2..) what is faster?"
date: 2010-11-17
forum: General Help
---

### Post by Cool Javelin on 2010-11-17
If I use the entire hard disk, is it necessary to have a numbered partition?

Is it faster or slower or does it even matter about the speed. (I know the speed may be negligible, but this question is somewhat theoretical.)

Does setting up a "numbered" partition take some space?

When using parted, it sometimes tell me the partition start/end settings are not "optimal" What does this mean?

Hello fellow Ubuntonions:

I have several hard disks, and note some have numbered partitions and it looks like some don't. I am sure I somehow goofed when setting them up.

For example: (assume /dev/ prepended to all the following...)
I have sda1, sda2, sda5 (swap.)

I also have sdb1  (note the one here)

I also have sdc (no number 1), sdd1, and sde1.

All sdc, sdd, and sde are setup to use the entire drive as one partition. (not one partition spread over 3 dives, 3 separate partitions, one per drive.)

I am able to mount all these and use with seemingly no problems.

sudo mount /dev/sdc /MyDriveC
sudo mount /dev/sdd1 /MyDriveD
etc...

Thanks, Mark.

---

### Post by Cool Javelin on 2010-11-17
Some new information:

parted on /dev/sdc (the one without the number) reports the start is at 0.00 and the end is at 80.0GB.

On /dev/sde (one with a number) it reports the start at 32.2Kb (not zero) and end at 15.0GB

In fact, all partitions with a number have a starting number not zero. Only the drive without a number starts at zero.

Also, sdc, when using 'p' (print partition) says partition 1 even though I don't use a 1 in the mount command. This may be due to the way parted was written.

(parted) p all
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  80.0GB  80.0GB  ext2


Model: ATA WDC WD150EB-00BH (scsi)
Disk /dev/sde: 15.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.0GB  15.0GB  primary  ext2


Model: ATA QUANTUM FIREBALL (scsi)
Disk /dev/sdd: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  40.0GB  40.0GB  primary  fat32        boot, lba


Model: ATA STI Flash 7.3.0 (scsi)
Disk /dev/sdb: 1025MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1020MB  1020MB  primary  ext2


Model: ATA STI Flash 7.3.0 (scsi)
Disk /dev/sda: 1025MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type      File system     Flags
 1      1049kB  910MB   909MB  primary   ext2            boot
 2      911MB   1024MB  113MB  extended
 5      911MB   1024MB  113MB  logical   linux-swap(v1)


M.

---

