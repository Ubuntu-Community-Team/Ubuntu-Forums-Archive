---
title: "Format USB drive set non-bootable"
date: 2010-09-27
forum: General Help
---

### Post by Merthod on 2010-09-27
Hi, the title is quite descriptive to what I want to do. I made a bootable Ubuntu installation within my USB stick but now I want to delete it. 

First I tried deleting all hidden and no-hidden files and folders but obviously I need to reset the MBR or something.

In System->Administration->Disk Utility I formatted the drive having now a blank device (FAT), but still the Ubuntu image is mounted.

Then I clicked on 'Edit Partition' and uncheck the Bootable checkbox but it returns an error (whether mounted or unmounted the drive is).

This is the return log file of the error:
> Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sdd, start=19456, new_start=19456, new_size=4013917184, type=0x0b
Entering MS-DOS parser (offset=0, size=4022337024)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 4022129664, type 0x0b)
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
Couldn't find partition to change


How do I completely format the drive removing this bootable Ubuntu installation? Please help

---

### Post by C.S.Cameron on 2010-09-27
Have you tried gparted?
It is available in Accessories/Ubuntu Software Center.
Reformat FAT32 and remove the boot flag.

---

### Post by Merthod on 2010-09-27
Yes I have tried now with no luck. I formatted it to nothing first and now only the Ubuntu boot loader appears, it's kind of annoying :confused:. GParted didn't touch the MBR

---

### Post by luvshines on 2010-09-27
Can you try this:

parted <device> set <partition-no> boot off

---

