---
title: "Partition Problems"
date: 2009-07-22
forum: General Help
---

### Post by dwally89 on 2009-07-22
Hi,

When I open GParted, it reports all of my disk as being unallocated, and in the terminal it says "Cannot have overlapping partitions."

How do I restore my partition table?

Thanks

---

### Post by gastly on 2009-07-22
You can try the following command to see your partition table. Sometimes Gparted does the same thing to me too, no partition table...I recommend that you **do not** fiddle with gparted trying to restore the partition table. I did that once and lost everything. Since, if your computer boots up and nothing is wrong, you probably have a working partition table.

Can you please clarify what you're tryng to do? Create a new partition?
And btw, you can use the following command to see your partition table in a terminal:
```

sudo fdisk -l

```

---

### Post by dwally89 on 2009-07-22
I'm not actually trying to do anything at the moment, but at some point in the future I might need to use GParted. How can I fix this?

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        9469        9730     2096128    c  W95 FAT32 (LBA)
/dev/sda2             976        7380    51448162+   7  HPFS/NTFS
/dev/sda3   *          12         975     7743330   83  Linux
/dev/sda4            7381        9730    18869782    f  W95 Ext'd (LBA)
/dev/sda5            7381        8910    12289660   83  Linux
/dev/sda6            8911        9442     4273256   83  Linux
/dev/sda7            9443        9468      208812   83  Linux
/dev/sda8            9469        9730     2096128    c  W95 FAT32 (LBA)

Partition table entries are not in disk order

```

---

### Post by gastly on 2009-07-22
> Partition table entries are not in disk order
That last line could be the cause of gparted not showing the partitions. And also, it could be 'cause you have two active boot partitions on the same hard disk...try unflagging the partition as a 'boot' partition (where no bootloader is installed)...that **might** help, but I'm not sure.

Also, I found a couple of posts that might interest you about this, they tell how to fix the problem:
[http://ubuntuforums.org/showthread.php?t=108649](http://ubuntuforums.org/showthread.php?t=108649)
[http://ubuntuforums.org/showpost.php?p=5446695&postcount=6](http://ubuntuforums.org/showpost.php?p=5446695&postcount=6)

**But**, I really don't recommend change the partition table in any way, unless you're having problems. When in the future you wish to add new partitions or something, **only then** try to fiddle with it.

---

### Post by dwally89 on 2009-07-22
So I did that, and now my partition table looks like this:

```
sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          12         975     7743330   83  Linux
/dev/sda2             976        7380    51448162+   7  HPFS/NTFS
/dev/sda3            7381        9730    18869782    f  W95 Ext'd (LBA)
/dev/sda4   *        9469        9730     2096128    c  W95 FAT32 (LBA)
/dev/sda5            7381        8910    12289660   83  Linux
/dev/sda6            8911        9442     4273256   83  Linux
/dev/sda7            9443        9468      208812   83  Linux
/dev/sda8            9469        9730     2096128    c  W95 FAT32 (LBA)

```

But I still get the overlapping partitions error from GParted.
How do I fix this?

---

### Post by gastly on 2009-07-22
hmmm...from the partition table, it seems that there are two active boot partitions on your hard disk (sda1 and sda4).
*EDIT*: Note the '*' under the 'boot' column, that tells you that the partition has bootable flag turned on.

As far as I know, you only should have 1 partiton as active boot partition.
So, what you should do is, leave the partition that you use to load the bootloader (it should be sda1 in your case...but you should check yourself) and unmark the other partition (sda4?) as boot.

```

sudo fdisk /dev/sda

```

and then enter 'p' to print the partiton table.

after that press 'a' and enter the partition number you wish to unmark as bootable. So, if you want to unmark 'sda4' as bootable, enter '4'.

**NOTE:** Don't do that in a hurry, take your time...if you unmark the wrong partition, and make your system unbootable, then don't panic, use the live cd and do the same steps to make the partition 'bootable' again.

---

### Post by dwally89 on 2009-07-22
OK, I did that but GParted still complains about Cannot Have Overlapping Partitions.

I think it might have something to do with sda8 (MEDIADIRECT), as when I am in nautilus, it appears there twice.

Any ideas?

---

### Post by gastly on 2009-07-22
hmmm...I think I got it. Look at these two lines:
```

/dev/sda4   *        9469        9730     2096128    c  W95 FAT32 (LBA)
/dev/sda8            9469        9730     2096128    c  W95 FAT32 (LBA)

```

See? both have the same start and end addresses (?). So, maybe if you corrected that, then the error would go. Maybe try backing up the data and removing the partition which is less important to you?

You can use fdisk to remove the partition. Be sure to unmount it if it's already mounted.

---

### Post by dwally89 on 2009-07-22
> **gastly said:**
> hmmm...I think I got it. Look at these two lines:
```

/dev/sda4   *        9469        9730     2096128    c  W95 FAT32 (LBA)
/dev/sda8            9469        9730     2096128    c  W95 FAT32 (LBA)

```

See? both have the same start and end addresses (?). So, maybe if you corrected that, then the error would go. Maybe try backing up the data and removing the partition which is less important to you?

You can use fdisk to remove the partition. Be sure to unmount it if it's already mounted.

Damn it, I really thought that would work. I removed sda8, rebooted, and then guess what... GParted complains of the same thing again!

What else could be wrong?

---

### Post by gastly on 2009-07-22
can you please post the partition table again? Let's see how it looks now.

---

### Post by dwally89 on 2009-07-22
```
sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          12         975     7743330   83  Linux
/dev/sda2             976        7380    51448162+   7  HPFS/NTFS
/dev/sda3            7381        9730    18869782    f  W95 Ext'd (LBA)
/dev/sda4            9469        9730     2096128    c  W95 FAT32 (LBA)
/dev/sda5            7381        8910    12289660   83  Linux
/dev/sda6            8911        9442     4273256   83  Linux
/dev/sda7            9443        9468      208812   83  Linux

```.

---

### Post by gastly on 2009-07-22
The partition table look good, without any errors imo.
Maybe someone with more knowlegde about partitions could tell you what's wrong with it. In the meantime, you can use fdisk to create and delete partitions.
Gee...I'm all lost with this lol

---

### Post by dwally89 on 2009-07-22
Anyone else got any ideas?

---

### Post by dwally89 on 2009-07-23
OK, I tried to use testdisk to fix my partition table, and now my partition table looks like this:

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          11       88326    6  FAT16
/dev/sda2              12         975     7743328   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3             976        7380    51448156+   7  HPFS/NTFS
/dev/sda4            7381        9730    18876375    f  W95 Ext'd (LBA)
/dev/sda5            7381        8910    12289660   83  Linux
/dev/sda6            8911        9442     4273256   83  Linux
/dev/sda7            9443        9468      208812   83  Linux
/dev/sda8            9469        9730     2096128    c  W95 FAT32 (LBA)
```

and GParted still says:

```
Cannot have a partition outside the disk!
```

What to do?

---

### Post by dwally89 on 2009-07-23
I'm not quite sure what I did, but I fixed it!

My partition table now looks like this:

```
sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          12         975     7743330   83  Linux
/dev/sda2             976        7380    51448162+   7  HPFS/NTFS
/dev/sda3            7381        9730    18869782    f  W95 Ext'd (LBA)
/dev/sda5            7381        8910    12289660   83  Linux
/dev/sda6            8911        9442     4273256   83  Linux
/dev/sda7            9443        9468      208812   83  Linux
/dev/sda8            9469        9730     2096128    c  W95 FAT32 (LBA)

```

And GParted runs with no problems

---

### Post by gastly on 2009-07-23
good thing you got it fixed :)
Nice work =D>

---

### Post by emeraldgirl08 on 2009-07-23
> I'm not quite sure what I did, but I fixed it!

:D

I get a lot of these too!

Congratulations!

---

### Post by dwally89 on 2009-07-23
Thanks.
I also finally deleted my Dell Utility and Media Direct partitions too.

---

