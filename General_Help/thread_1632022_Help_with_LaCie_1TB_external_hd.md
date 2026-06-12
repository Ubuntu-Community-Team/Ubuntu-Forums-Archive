---
title: "Help with LaCie 1TB external hd"
date: 2010-11-27
forum: General Help
---

### Post by shayli147 on 2010-11-27
Hi!
I recently received a LaCie 1TB external hard disk (from the neil poulton design series), and I am having some trouble setting it up.
The software that comes with it seems to be compatible only with windows and osx, so I tried to format it using Disk Utility (to ext4). However, when I click "create" in the "create partition" dialog I receive an error:
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdf, start=349936128, size=999854949888, type=0x83
Entering MS-DOS parser (offset=0, size=1000204886016)
MSDOS_MAGIC found
looking at part 0 (offset 339451392, size 10484736, type 0x0c)
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
Error: Too many primary partitions.
ped_disk_add_partition() failed
```Is there any other way to format the partition? Or is there something I should do before?
I should mention that Ubuntu doesn't recognize any other partition besides the 10MB software (out of 1TB).

Thanks for helpers! :D
Shay-li

---

### Post by dino99 on 2010-11-27
in case:

sudo dmraid -rE

then:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by shayli147 on 2010-11-29
thank you^^
the error msg is gone now, but i still cannot copy into my external hd...
the msg i get this time is:
```
[B]
Error while copying.[/B]
 The folder "Songs" cannot be copied because you do not have permissions to create it in the destination.

```or in another form:
```

**Error while copying "IMG_3662.JPG".**
 There was an error copying the file into /media/Appushin.
 Show more detailes:
 Error opening file '/media/Appushin/IMG_3662.JPG': Permission denied

```the question is... how do i get the permission? x.x

---

### Post by shayli147 on 2010-12-02
hmpf?^^"

---

