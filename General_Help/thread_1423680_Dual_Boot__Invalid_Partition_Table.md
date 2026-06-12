---
title: "Dual Boot : Invalid Partition Table"
date: 2010-03-06
forum: General Help
---

### Post by kogger on 2010-03-06
I'm trying to install Windows XP Pro Performance on my laptop, dual-booting it with Ubuntu 9.10. But after installing XP, I get an "invalid partition table" error after my computer reboots. Booting off a live cd, I think the problem is that both my linux and windows partitions are flagged as bootable, but I get an error when trying to remove the bootable flag from the linux partition:

```
Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sda, start=32256, new_start=32256, new_size=201642706944, type=0x05
Entering MS-DOS parser (offset=0, size=320072933376)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 201642706944, type 0x05)
Entering MS-DOS extended parser (offset=32256, size=201642706944)
readfrom = 32256
MSDOS_MAGIC found
readfrom = 85896599040
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 1 (offset 201642739200, size 117243141120, type 0x07)
new part entry
looking at part 2 (offset 318885880320, size 1184440320, type 0x82)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
Couldn't find partition to change
```

Here's the results of sudo fdisk -l:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000901c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24515   196916706    5  Extended
/dev/sda2   *       24516       38769   114495255    7  HPFS/NTFS
/dev/sda3           38770       38913     1156680   82  Linux swap / Solaris
/dev/sda5               1       10443    83883334+  83  Linux
/dev/sda6           10444       24515   113033308+  83  Linux
```

I'm tempted to re-write the partition table with gpart, but the man page says that it often fails with extended partitions, so I'm hesitant.

Any suggestions?

---

### Post by dcstar on 2010-03-06
> **kogger said:**
> I'm trying to install Windows XP Pro Performance on my laptop, dual-booting it with Ubuntu 9.10. But **after installing XP**, I get an "invalid partition table" error after my computer reboots. Booting off a live cd, I think the problem is that both my linux and windows partitions are flagged as bootable, but I get an error when trying to remove the bootable flag from the linux partition:

```

.........
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24515   196916706    5  Extended
**/dev/sda2 **  *       24516       38769   114495255    7  HPFS/NTFS
/dev/sda3           38770       38913     1156680   82  Linux swap / Solaris
/dev/sda5               1       10443    83883334+  83  Linux
/dev/sda6           10444       24515   113033308+  83  Linux
```

I'm tempted to re-write the partition table with gpart, but the man page says that it often fails with extended partitions, so I'm hesitant.

Any suggestions?

You wedged in a new partition after Linux was installed so any settings in the original Grub config are probably now incorrect.

Do a search for manually modifying your version of Grub and you should find some instructions to fix things.

---

