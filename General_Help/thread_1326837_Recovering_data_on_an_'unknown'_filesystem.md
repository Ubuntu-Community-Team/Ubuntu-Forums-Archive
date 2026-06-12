---
title: "Recovering data on an 'unknown' filesystem?"
date: 2009-11-14
forum: General Help
---

### Post by dwdude on 2009-11-14
So here's my problem.

Last night, I was shrinking my Vista drive in order to make another partition for XP last night. The problem is, this dumb HP laptop NEVER keeps the charger in all the way, it always seems to fall out. So during the shrinking process, the laptop died. Gparted says that the partition has an unknown filesystem.

```
david@megatron:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x122cd09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20313   163163132    7  HPFS/NTFS
/dev/sda2           20314       25993    45624600    7  HPFS/NTFS
/dev/sda3           25994       27209     9767520   83  Linux
/dev/sda4           27210       30401    25639740    5  Extended
/dev/sda5           29904       30401     4000185   82  Linux swap / Solaris
/dev/sda6           27210       29902    21631459+  83  Linux

Partition table entries are not in disk order

```

/dev/sda1 is vista.
/dev/sda2 is a drive I made to store stuff a while back.
/dev/sda3 is /.
/dev/sda6 is /home.

```
david@megatron:~$ sudo mount -t ntfs /dev/sda1 /media/please -r
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

I'm interested in possibly being able to read from sda1 to see if I can recover files, and if so, recover them. I have a lot of things on there that would be really unfortunate to have to redo. But if I can't recover, then I guess I'll reformat.

fdisk seems to say that sda1 is ntfs (which it is), but mounting it fails.

When trying to boot into Vista, I believe I got an error saying "unusable executable type" or something to that effect, bringing me back to the grub menu.

Any suggestions or ideas?

---

### Post by Joe Ker1086 on 2009-11-14
download [test disk]("http://www.cgsecurity.org/wiki/TestDisk") it is good at a couple things and can make partitions bootable again (that can get pretty advaced/ugly if you do something wrong) but it also has some file recovery tools. Test disk can find files and it comes with photorec which can find more than just pictures.... i would go with testdisk to get files if you have a a couple files in specific you want to find or use photorec if you want to pull back EVERYTHING that was on the drive (for the most part) warning tho, if u use photo rec it will pull back a whole lot of data you might not want to sort through....

---

### Post by dwdude on 2009-11-14
Thank you very much for the fast reply! I will look into TestDisk and see if it can help me out, then post back here.

---

### Post by dwdude on 2009-11-14
Ummmm. Does anyone know if you can undo the "Write to partition table" function it has? I believe it just rewrote my partition table and only put in the faulty partition, which still can't be read. 

```
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - ATA Hitachi HTS54252

Partition table type (auto): Intel
Disk /dev/sda - 250 GB / 232 GiB - ATA Hitachi HTS54252
Partition table type: Intel

Analyse Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 07
NTFS at 20313/0/1
Info: size boot_sector 91249193, partition 91249200
get_geometry_from_list_part_aux head=255 nbr=8
get_geometry_from_list_part_aux head=8 nbr=2
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=255 nbr=8
Current partition structure:
Invalid NTFS boot
 1 * HPFS - NTFS              0  32 33 20312 254 30  326326264
 1 * HPFS - NTFS              0  32 33 20312 254 30  326326264
 2 P HPFS - NTFS          20313   0  1 25992 254 63   91249200 [Documents]
 3 P Linux                25993   0  1 27208 254 63   19535040
 4 E extended             27209   0  1 30400 254 63   51279480
 5 L Linux Swap           29903   0  1 30400 254 63    8000370
   X extended             27209   0  2 29901 254 63   43263044
 6 L Linux                27209   2  1 29901 254 63   43262919
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
NTFS at 0/1/1
filesystem size           389126367
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               24320397
clusters_per_mft_record   -10
clusters_per_index_record 1
   D HPFS - NTFS              0   1  1 24221 254 63  389126367
     NTFS, 199 GB / 185 GiB
Search for partition aborted
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

Results
   * HPFS - NTFS              0   1  1 24221 254 63  389126367
     NTFS, 199 GB / 185 GiB

interface_write()
 1 * HPFS - NTFS              0   1  1 24221 254 63  389126367
write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition
You will have to reboot for the change to take effect.

... Further down in the log ...

Analyse Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * HPFS - NTFS              0   1  1 24221 254 63  389126367

```

I really don't think rebooting would be a very good idea right now.

---

### Post by dwdude on 2009-11-14
I just used fdisk to change the partition table.

Good thing I listed my table in the first post or that would have been less fun :)

Still unable to view contents of sda1, however. Anybody?

---

