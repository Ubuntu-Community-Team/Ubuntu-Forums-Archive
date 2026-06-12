---
title: "Random Hidden Partiion?"
date: 2010-06-06
forum: General Help
---

### Post by dewey_daniels on 2010-06-06
Well I was going through my disk utilty and notices a random 150 gig partition. I don't think that is my linux partition but I still cant delete it. With only 500gigs I don't want to waste that much space.

PS Isn't the second one without the error the linux partition?

---

### Post by lavinog on 2010-06-07
Can you post the output of 
```

sudo fdisk -l /dev/sda

```

It could be that your linux partitions are logical partitions that exist in an extended partition, and it is the extended partition you are seeing.

[img]http://ubuntuforums.org/attachment.php?attachmentid=159613&stc=1&d=1275885797[/img]
Notice how the extended partition contains the other partitions.

If you do need to resize it, you will need to do it from the live cd.

---

### Post by dewey_daniels on 2010-06-07
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1531       22671   169809062    7  HPFS/NTFS
/dev/sda2           41220       60802   157286400    7  HPFS/NTFS
/dev/sda3           22671       41220   148998145    5  Extended
/dev/sda5           22671       40462   142906368   83  Linux
/dev/sda6           40462       41220     6090752   82  Linux swap / Solaris

Partition table entries are not in disk order
derek@derek-laptop:~$

---

### Post by lavinog on 2010-06-07
Which partition are you wondering about?
It looks like you have 2 ntfs partitions (sda1 & 2), a linux partition (sda5) inside an extended partition (sda3), and a swap partition (sda6)

sda3 is like a container for sda5, It isn't wasting any space.
Extended partitions are used to work around a limit of 4 primary partitions.
If you wanted to add an additional partition, it would have to go inside the extended partition.

---

### Post by dewey_daniels on 2010-06-07
Then why can't I see or store things on SDA3

---

### Post by lavinog on 2010-06-07
> **dewey_daniels said:**
> Then why can't I see or store things on SDA3

Because it doesn't take up space on your hd:
```

/dev/sda3 22671 41220 148998145 5 Extended
/dev/sda5 22671 40462 142906368 83 Linux

```
sda5 is where you store your files, and is contained in sda3
There does seem to be some free space at the end:
41220 - 40462 = 758 cylinders
758 * 8225280 =~ 6G
So you can gain about 6G of space if you extend the size of sda5 to the end of sda3
You can do this with the partition editor (gparted) on the live cd.
I have never had a problem with resizing a partition, but just to be safe, you should backup your stuff before you do.

---

