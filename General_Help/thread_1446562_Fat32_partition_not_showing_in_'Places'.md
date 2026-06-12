---
title: "Fat32 partition not showing in 'Places'"
date: 2010-04-04
forum: General Help
---

### Post by Diptansu on 2010-04-04
I am using Koala .. Fresh installation.

Other than the Linux root and SWAP I have --

1) About 36 GB

2) About 100 GB

3) About 90 GB

4) About 200 GB

four partitions. All of them ar fat32 format.

First 3 are showing in the 'places' and being Mounted properly.

But the forth partition (200 GB one) is not showing in 'Places'.

How can I mount the forth one?

Its Showing in my 'sudo fdisk -l'

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbae8a3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4699    37744686    b  W95 FAT32
/dev/sda2            4700       60801   450639315    5  Extended
/dev/sda5            4700        9398    37744686   83  Linux
/dev/sda6            9399       22452   104856223+   b  W95 FAT32
/dev/sda7           22453       48560   209712478+   b  W95 FAT32
/dev/sda8           48561       60309    94373811    b  W95 FAT32
/dev/sda9           60310       60801     3951958+  82  Linux swap / Solaris


```

Please help me .. :(

---

### Post by gastly on 2010-04-04
It could be that the partitions that are not being shown are not there in the fstab file.
Please paste the contents of the file: **/etc/fstab** :)

---

### Post by Diptansu on 2010-04-04
Acctually nothing was shown in /etc/fstab .. :(

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6a53f90c-de75-4c6b-9daf-101dfb6d1fdd /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=4595267c-c538-4455-881e-61d7aa1c85d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Diptansu on 2010-04-04
Also the drive is not showing in system > administration > system monitor > File system TAB

The only place it is showing is in fdisk -l !!

---

### Post by dunkar70 on 2010-04-04
Try this...

```
sudo mount /dev/sda7 /mnt/sda7
```Make sure the mount point (/mnt/sda7) exists first.

---

### Post by dunkar70 on 2010-04-04
The responses do not seem to support your original question. What exactly are you trying to do? Are you trying to get the partition to show up in Places menu or to be mounted automatically every time you boot up? Do you not care as long as you can access the data?

Partitions mounted via fstab will not show up in places, they will simply be part of the file system at the mount point.

The Places menu shows:

[LIST=1]
[*]Partitions and drives not listed in fstab that you can mount manually be executing a command or trying to access the drive via Nautilus. In your case, there seems to be a problem with sda7 not appearing here.
[*]Folders that have been bookmarked. They must be part of the file system before they can be bookmarked.
[/LIST]
I have a separate reply that covers manually mounting the partition. Otherwise, enter a new line in your fstab file that reads something like:
```
/dev/sda7       /mnt/sda7     vfat    auto,sync,rw,uid-1000,gid=1000,umask=007   0   0
```
You can also bookmark the location to make it easier to access, even from the Places menu.

---

### Post by Diptansu on 2010-04-04
> **dunkar70 said:**
> Try this...

```
sudo mount /dev/sda7 /mnt/sda7
```Make sure the mount point (/mnt/sda7) exists first.

here it is what I found ..

```
dips@AztecZ:~$ sudo mount /dev/sda7 /mnt/sda7
[sudo] password for dips: 
mount: you must specify the filesystem type
```

---

### Post by Diptansu on 2010-04-04
Did I made any mistake while installing ubuntu? Such as I didnt format the drive something like that?

But in 'fdisk -l' its showing fat32 file system .. !!
(/dev/sda7           22453       48560   209712478+   b  W95 FAT32)

What should I do .. :(

---

### Post by Diptansu on 2010-04-04
Well .. now I went to System > Administration > Disk Utility

Here it was showing the 200 GB partition but the file system was 'unrecognized'

So I deleted the partition .. and when I tried to create a new one it said ..

```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=184674018304, size=214745610752, type=0x0c
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 38650558464, type 0x0b)
new part entry
looking at part 1 (offset 38650590720, size 461454658560, type 0x05)
Entering MS-DOS extended parser (offset=38650590720, size=461454658560)
readfrom = 38650590720
MSDOS_MAGIC found
readfrom = 77301181440
MSDOS_MAGIC found
readfrom = 399419596800
MSDOS_MAGIC found
readfrom = 496058411520
MSDOS_MAGIC found
readfrom = 184674018304
MSDOS_MAGIC found
readfrom = 184673986560
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
got disk
new partition
Error: Can't have overlapping partitions.
ped_disk_add_partition() failed

```

What does it men by 'overlapping partitions'? Hope this gives you some clue to solve the problem .. :-/

---

