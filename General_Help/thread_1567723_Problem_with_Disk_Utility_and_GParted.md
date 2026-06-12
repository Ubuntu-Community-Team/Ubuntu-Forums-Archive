---
title: "Problem with Disk Utility and GParted"
date: 2010-09-04
forum: General Help
---

### Post by SuperDuckk on 2010-09-04
Hi guys,

I found Disk Utility modifies partition sizes without our request. When you try to change the partition type, it somehow modifies the size by rounding it (MiB, or Cylinders?).

I copied a damaged partition which is 245760000 sectors, to a new disk. Tried to modify the partition type using Disk Utility, it gave the error below, and the last sector is changed from 245762047 to 245762369, without even noticing me.

```

Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sdb, start=1048576, new_start=1048576, new_size=125829120000, type=0x07
Entering MS-DOS parser (offset=0, size=1000204886016)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 125829120000, type 0x83)
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
got partition
changed partition to start=1048576 size=125829284864
committed to disk
ugh, offset or size changed
offset:     1048576
size:       125829120000
new_offset: 1048576
new_size:   125829284864

```

Luckily noticed the change and I had the original sectors noted down somewhere.

This should go into the bug reports for Disk Utility, if someone please.

I found Disk Utility and GParted are not yet functional enough to be an alternative to the fdisk command. GParted doesn't even display the partition type anywhere (rather it displays the FS type if there is one) and they both use GiB as units, which is smaller resolution, making it impossible to work with exact sector sizes.

Ok, even fdisk is a bit aged to work with LBA sizes (it shows sizes in blocks, which don't match 512 byte sectors) but I think it's still the most usable one for partitioning.

I believe in the importance of well designed GUI tools. As much as possible things should be doable in GUI, which gives a better presentation of the data, and lets the user see what things they can do at a first glance.

---

