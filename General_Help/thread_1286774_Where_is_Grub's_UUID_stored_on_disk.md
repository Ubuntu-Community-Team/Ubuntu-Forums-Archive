---
title: "Where is Grub's UUID stored on disk?"
date: 2009-10-09
forum: General Help
---

### Post by GrayBear on 2009-10-09
I would like to know where are the UUID strings stored on hard disk.
Grub's menu.lst use the UUID strings, and I guess it doesn't look into /etc/blkid.tab
I checked the first sector (512 Bytes) of the partitions, and the UUID is not there. I am sure about that, because the first 512 Bytes of a swap partition are 0.
UUID's can't be stored in the MBR of the hard disk, so I guess they are stored into the first 30 KB of the hard disk, where Grub stage 1.5 is stored?

or UUID's are made from the hard disks Serial Numbers, and therefore can't be changed?

thanks

---

### Post by sisco311 on 2009-10-09
You can change the UUID with tune2fs. For more info, please read the man page.

---

### Post by GrayBear on 2009-10-09
Checked that. Says:
[COLOR=Silver][COLOR=Black]"Instead  of  specifying a device name directly, external-journal can also be specified by either LABEL=label or UUID=UUID to locate the external journal by  either  the  volume  label  or  UUID **stored in the ext2 superblock at the start of the journal**."[/COLOR]
[/COLOR]
But blkid command shows UUID for other partitions than ext2fs too.
/dev/sda1: UUID="BC042E1F042DDCE0" TYPE="ntfs" 

that means, UUID is **NOT** something that only ext2fs partitions have. Swap and NTFS partitions have UUID's too. Where is the UUID stored in a NTFS partition then?

---

### Post by sisco311 on 2009-10-09
> **GrayBear said:**
> 
that means, UUID is **NOT** something that only ext2fs partitions have. Swap and NTFS partitions have UUID's too. Where is the UUID stored in a NTFS partition then?

Check this out: [http://en.wikipedia.org/wiki/GUID_Partition_Table#Partition_entries_.28LBA_2.E2.80.9333.29]("http://en.wikipedia.org/wiki/GUID_Partition_Table#Partition_entries_.28LBA_2.E2.80.9333.29")

H.T.H.

---

### Post by v.cecchetto on 2009-10-28
We need to agree in which way indicate a byte over an hard disk.

Find how many bytes my pendrive contains:

$ sudo fdisk -lu /dev/sdb

> .... total 511232 sectors

Now, every sector is made of 512 bytes (usually).

So my pendrive is made of 

 511232 * 512 = 261750784 bytes

Ok. Let's indicate the first sector LBA 0.

The last sector of my pendrive is LBA 511231.

To indicate one byte in 512 bytes of a sector i use hexadecimal notation (use the ubuntu calculator to convert from decimal representation to hex and back)

0x000 = byte #1
0x001 = byte #2
0x002 = byte #3
...
0x00a = byte #11
...
0x010 = byte #17
...
0x1fe = byte #511
0x1ff = byte #512

This notation is useful when you use an hex editor to navigate into bytes of your disk.

Ok. Now I can indicate every single byte on the pendrive with its proper name:

LBA 13423 - 0x1a0 

To indicate the byte contents i use the hex representation:

- a byte is a sequence of 8 bit: 01011010  

- we need two hex number:  5a

(use the ubuntu calculator to convert from binary representation to hex and back)

A note: from now we suppose we are working with MBR partition and not GPT partition.

Every MBR disk has its proper Disk Identifier.
([http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record))

This name is stored in the so called MBR sector (LBA 0):

Optional Disk signature

Sector: LBA 0 
Bytes:  from 0x1b8 to 0x1bb

(es. my pendrive:
LBA 0 - 0x1b8: e1
LBA 0 - 0x1b9: 8f
LBA 0 - 0x1ba: 0c 
LBA 0 - 0x1bb: 00

$ sudo fdisk -lu /dev/sdb

> ... disk identifier: 0x000c8fe1

Is little endian representation (google for it).

One disk -> one disk identifier 

Now partition.

Every partition has its proper file system (fat32, ntfs, ext3, hfs+...).

When a partition is created, a place over the hard disk is allocated to that partition. 

$ sudo fdisk -lu /dev/sdb1

> /dev/sdb1               63      511231      xxx xxx xxx

My first partition goes from sector LBA 63 to sector LBA 511231 and is FAT32.

Every FAT32 partition has its proper ID (serial number).
([http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table))

This name is stored in the first sector of the partition:

Sector: LBA 63
Bytes: from 0x043 to 0x046

(es. my pendrive:
LBA 63 - 0x043: a2
LBA 63 - 0x044: ae
LBA 63 - 0x045: 5e 
LBA 63 - 0x046: 3f

$ blkid

> /dev/sdb1: UUID="3F5E-AEA2" TYPE="vfat" 

One FAT32 partition -> One Identifier

... I stop here. I tell you only that also an EXT3 partition stores its own partition ID in the first sectors of the partition.

GPT partition:

1. Every disk has its proper Disk GUID (LBA 1 - bytes: 0x38 - 0x47), LBA 0 is not (to be) used. ([http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table))

2. Every partition:

- like before, you find in the first sectors of the partition its Identifier -> FAT32 create it so you find it in the first sector of the partition

- plus you have another identifier, the Partition unique GUID -> GPT create it so you find it in the GPT partition table entry for that partition, usually  LBA 2 (bytes: 0x10 - 0x1f)
You can't use fdisk to find it but you have to use gdisk:

$ sudo gdisk /dev/sdb

at the prompt press > i

You can see also the Partition type GUID. It is a long string to simply indicate the type of the partition.

Partition Label and attributes are another story... :)

---

### Post by motosauro on 2010-08-06
> **v.cecchetto said:**
> 
cut ...
Partition Label and attributes are another story... :)

Sry for reviving an old thread, but this post is awesome.
I'm preparing all my gentoo boxes for the shift to UUIDs or LABELS and I was looking for documentation. I found this post looking for an explanation about where the UUID was stored and now I know.
Thanks for the wonderful post v.cecchetto :)

---

