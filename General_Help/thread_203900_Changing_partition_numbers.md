---
title: "Changing partition numbers"
date: 2006-06-26
forum: General Help
---

### Post by Zalbor on 2006-06-26
I want to create a new partition on my hard drive, by resizing my / partition which is much bigger than I need. However, by doing this the partition number of my swap will change from sda8 to sda9.
My question is: What files in my system should I redirect to sda9, so that after the repartitioning it will load swap normally? Is fstab all I need to change?

Here's the output of "sudo fdisk -l /dev/sda".
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7491    60171426    7  HPFS/NTFS
/dev/sda2            7492       14589    57014685    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            7492       11061    28675993+   7  HPFS/NTFS
/dev/sda6           11062       12366    10482381   83  Linux
/dev/sda7           12367       14494    17093128+  83  Linux
/dev/sda8           14495       14589      763056   82  Linux swap / Solaris
```
(I don't know what it means by "Partition 2 does not end on cylinder boundary", but I haven't had any problems with the hard drive so far).

And this is fstab:
```
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       /win/BACKUP     ntfs    umask=0222,nls=utf8        0       0
/dev/hda1       /win/WIN98      vfat    umask=000,utf8        0       0
/dev/sda1       /win/WINXP      ntfs    umask=0222,nls=utf8        0       0
/dev/sda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
```

---

### Post by matrooswolf on 2006-06-26
I had the same kind of problem, after repartitioning, swap was disabled, I just updated the partition numbers in fstab, and everything worked fine.

just my 2 cents (there are a lot more experienced partition know it all guys out there then me!, and I do not know about the cylinder boundary thing)

But you do have a lot of partitions, time for a cleanup?

This I found explains partitioning well:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
(credits to Aysiu)

---

### Post by Zalbor on 2006-06-26
Thanks for your reply.
If yours worked by changing just fstab, I guess that's all that needs to be changed. But I'll wait a bit more, just to be sure. :)
As for the many partitions, they're not really that many.

---

### Post by scxtt on 2006-06-26
[quote=Zalbor]```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            7492       14589    57014685    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            7492       11061    28675993+   7  HPFS/NTFS
```[/quote]you have 2 partitions that start @ the same spot {7492} & "/dev/sda2" most likely ends in a weird, possibly random position -- is that a windows95 extended partition (W95 Ext'd (LBA))?

---

### Post by Zalbor on 2006-06-26
It's an extended partition, yes, and the rest are logical partitions inside it. I don't remember what I used to partition the disk when I first got it.

---

