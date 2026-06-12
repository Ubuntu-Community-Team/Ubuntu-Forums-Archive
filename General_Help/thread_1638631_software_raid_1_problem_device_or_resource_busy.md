---
title: "software raid 1 problem: device or resource busy"
date: 2010-12-05
forum: General Help
---

### Post by mdgtptrl on 2010-12-05
Hi,

I have 2, 2TB drives that I want to set up in RAID1. I plan to have a 1.5TB partition, and a 500GB partition on each 2TB drive. I'm on 10.10 desktop

I format both drives to free them up for the RAID array. In disk utility, I go to File->Create->RAID Array... and select both drives. Then I create the 1.5TB partition in the RAID1, which takes a while. When I go to create the other partition, it fails immediately with the error: "the operation failed." Details below.

Can I only have one volume per software RAID array? Why does it say the device is busy?

details: 
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/md0, start=1499999997952, size=500396151808, type=
Entering MS-DOS parser (offset=0, size=2000396149760)
MSDOS_MAGIC found
looking at part 0 (offset 1499999997952, size 500396150784, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
new partition
added partition start=1499999997952 size=500396150784
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 1 of size 1499999997952 at offset 500396150784 on /dev/md0: Device or resource busy

```

---

### Post by mdgtptrl on 2010-12-06
bump?

---

### Post by mdgtptrl on 2010-12-06
I'd really like to get this resolved. Anybody?

---

### Post by mercury80 on 2011-06-22
Still no solution? Want to create two striped raid with 2x2TB and a JBOD with 1.5TB + 2TB. But when i try to format the 4TB "disk" i get this:
```
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/dm-0, scheme=3
got it
got disk
committed to disk
BLKRRPART ioctl failed for /dev/dm-0: Invalid argument

```
There is no path like /dev/dm-0
The disk utility then says the "disk" has a GUID or MBR partition table. If i then try to create a partition i get this reslult: (it needs to be a NTFS-drive)
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/dm-0, start=0, size=4000795721728, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
Entering MS-DOS parser (offset=0, size=4000795721728)
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
got disk
new partition
added partition start=17408 size=4000795687424
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 1 of size 17408 at offset 4000795687424 on /dev/dm-0: Invalid argument

```

When using a MBR to create a NTFS partition this is the reslut:
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/dm-0, start=0, size=4000795721728, type=0x07
Entering MS-DOS parser (offset=0, size=4000795721728)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
got disk
new partition
Error: partition length of 7814048067 sectors exceeds the msdos-partition-table-imposed maximum of 4294967295
ped_disk_add_partition() failed

```

Dont know if it is of any help, but this is what happens when i create a ext4 partition.
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/dm-0, start=0, size=4000795721728, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
Entering MS-DOS parser (offset=0, size=4000795721728)
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
got disk
new partition
added partition start=17408 size=4000795687424
committed to disk
Error doing BLKPG ioctl with BLKPG_ADD_PARTITION for partition 1 of size 17408 at offset 4000795687424 on /dev/dm-0: Invalid argument

```

Anyone?

---

### Post by psusi on 2011-06-23
It looks like the disk utility does not understand dmraid devices.  Please file a bug report against it, and use gparted instead.  Also GPT is currently not supported on dmraid.  Unless you need to dual boot with windows, it is generally advisable to use Linux mdadm software raid instead of fakeraid, as it is better supported.  You will need to use the bios utility or dmraid -E to delete the fakeraid signatures from the drives, and reinstall with the alternate installer to setup software raid.

---

