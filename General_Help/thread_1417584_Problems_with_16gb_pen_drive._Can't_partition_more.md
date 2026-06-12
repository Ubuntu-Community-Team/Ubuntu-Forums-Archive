---
title: "Problems with 16gb pen drive. Can't partition more than 1gb."
date: 2010-02-27
forum: General Help
---

### Post by themusicalduck on 2010-02-27
I've been trying to partition my USB pen drive but for some reason it won't make a partition any bigger than 1 gig. The reason I formatted it was for compatibility with a friends Windows computer that wouldn't recognise it while it was NTFS (so I tried FAT16, but it still wouldn't recognise it for some strange reason.)

Anyway, after partitioning it to FAT, I partitioned it back to NTFS and shortly after tried to put Ubuntu onto it using unetbootin. During the writing process, Ubuntu locked up and I had to hard reset. (even the reisub trick did nothing) After restarting, I noticed the pen drive was showing as only 1gb big.

I don't really know if the crash caused it, because it might have been 1gb after I had reformatted to NTFS (I just didn't check).

I've since reformatted and repartitioned it using ext3/4, ntfs, FAT and it's the same every time. Also, I've tried to use unetbootin again on the 1gig partition, and it will work, but if I try to boot up off it on my netbook, it says "Missing operating system" and then boots off the hard drive.

Lastly, when I do format it, there doesn't seem to be any kind of permissions on the pen drive until I run chown on it. Then I can write to it normally.

This is a really strange problem.. I'm almost inclined to think the pen drive might just be broken and I'll need to take it back to the shop. (Withdrawing any information about the whole repartitioning it..)

I'm using gparted on 9.10 if it's relevant.

---

### Post by gadolinio on 2010-02-27
Don't know if this will work, but you could try opening gparted, and deleting al the partitions the pendrive has. That means you would have the whole 16GiB as "unallocated space". Then, create a new partition in FAT16 or FAT32. Maybe the latter works better and lets you create bigger partitions.
Hope this helps...

---

### Post by jamesisin on 2010-02-27
Just to be sure, you are using gparted and not the new Disk Utility?

If you partition with FAT there are no permissions nor ownership in that file system.  You may be changing owner for the *mount point*, however.

Take a look at that drive using some of the other tools available (Disk Utility, gparted, and Disk Usage Analyzer come to mind) and see what you see.

---

### Post by themusicalduck on 2010-02-27
I have been using gparted. I had a go at partitioning it with Disk Utility and it did exactly the same thing.

The permissions thing must have just been when I tried it with FAT then. But no matter what file system I try, it still will only make a 1gb partition (and leaves the rest as unallocated).

I have full write access to this 1gb partition, but there's 15gb of space that I can't use (and I really want to be able to use unetbootin and have it work too)

I always delete any existing partitions before trying to reformat it.

---

### Post by themusicalduck on 2010-02-27
I thought I'd try creating another partition after the 1gb partition had been created. From diskutils I got this ```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdd, start=1031781376, size=15116289023, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
Entering MS-DOS parser (offset=0, size=16148070400)
MSDOS_MAGIC found
found partition type 0xee => protective MBR for GPT
Exiting MS-DOS parser
Entering EFI GPT parser
GPT magic found
partition_entry_lba=2
num_entries=128
size_of_entry=128
Leaving EFI GPT parser
EFI GPT partition table detected
containing partition table scheme = 3
got it
Warning: Not all of the space available to /dev/sdd appears to be used, you can fix the GPT to use all of the space (an extra 29523969 blocks) or continue with the current setting? 
got disk
new partition
Error: Unable to satisfy all constraints on the partition.
ped_disk_add_partition() failed

```

I didn't get any error from gparted, except that it failed.

---

### Post by jamesisin on 2010-02-27
Can you locate this device under /dev?  This may help understand the problem better.

---

### Post by themusicalduck on 2010-02-27
It's there under /dev/disk

In by-id one says usb-Generic_Mass_Storage_1A47930C-0:0 and another usb-Generic_Mass_Storage_1A47930C-0:0-part1.

Not sure if that is useful though. I don't really know what information I'm looking for specifically in here.

---

### Post by jamesisin on 2010-02-27
That looks like the device and one partition on the device.  I just wanted to confirm that /dev was showing the same as what gparted and palimpsest were showing.  Have you tried deleting all the partition information, the MBR, and reformating the entire device?  Once Disk Utility shows the device in this way, it ought to show it as a 16gb device.

---

### Post by dcstar on 2010-02-28
> **themusicalduck said:**
> I thought I'd try creating another partition after the 1gb partition had been created. From diskutils I got this ```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdd, start=1031781376, size=15116289023, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
Entering MS-DOS parser (offset=0, size=16148070400)
MSDOS_MAGIC found
**found partition type 0xee => protective MBR for GPT**
..........

```

I didn't get any error from gparted, except that it failed.

Use the Partition Editor to write a new partition table (which will wipe the device).

---

### Post by garvinrick4 on 2010-02-28
I have screwed over a few of those flash drives myself goofing around with them. I always used gparted to reformat them. Had a puny little HP program for USB drives and it has worked for me when I get one bent out of shape. Try to google it and see if you can download it. Small file but seems to work.

---

### Post by themusicalduck on 2010-02-28
Thanks dcstar, your suggestion worked!

---

### Post by dcstar on 2010-02-28
> **themusicalduck said:**
> Thanks dcstar, your suggestion worked!

No worries, a lot of these USB devices come with specialised Windows-only software built into them on the assumption that EVERYBODY runs Windows.

Usually the only way to clean them up is to rewrite the partition table......

---

