---
title: "Can't partition external drive"
date: 2010-07-08
forum: General Help
---

### Post by savaan on 2010-07-08
I'm trying to format/repartition a 250 gig external Seagate drive. I get the following error:
```

Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdc, start=32256, size=250056705024, type=0x83
Entering MS-DOS parser (offset=0, size=250059350016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 250056705024, type 0x85)
Entering MS-DOS extended parser (offset=32256, size=250056705024)
readfrom = 32256
MSDOS_MAGIC found
readfrom = 373273722880
lseek failed (Invalid argument)
Exiting MS-DOS extended parser
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Can't have a partition outside the disk!
ped_disk_new() failed
```Am I missing something?

---

### Post by savaan on 2010-07-21
bumpity bump??

---

### Post by gordintoronto on 2010-07-21
Have you tried using Gparted?  (sudo gparted)

---

### Post by mr clark25 on 2010-07-21
it looks like the partition you are trying to make does'nt line up right with your hard drive. i would take gordintoronto's suggestion and use gparted.

---

### Post by savaan on 2010-07-23
awesome! thanks guys. gparted worked.

---

