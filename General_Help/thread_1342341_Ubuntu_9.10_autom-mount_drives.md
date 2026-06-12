---
title: "Ubuntu 9.10 autom-mount drives"
date: 2009-11-30
forum: General Help
---

### Post by anderskitson on 2009-11-30
I would like to automount two partitions on a drive on boot 

this is there their fdisk

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099e60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          67       93786   752805900   83  Linux
/dev/sda3           93787      182401   711799987+  83  Linux

```

I have tried editing the fstab by adding these lines

```
/dev/sda3       /media/Media    ext2   defaults   0     0
/dev/sda2       /media/Projects_Design  ext2   defaults   0    0
```

However this doesnt work on boot and my drives wont mount manually i get this error

mount: only root can mount /dev/sda3 on /media/Media

Below are images of disk utility showing the names of the drives and their locations for verification

[IMG]http://andcreate.com/ubuntu/Screenshot-1.png[/IMG]
[IMG]http://andcreate.com/ubuntu/Screenshot.png[/IMG]

---

