---
title: "Partition mounts, can not read or write"
date: 2009-07-25
forum: General Help
---

### Post by Atro on 2009-07-25
Hi Everyone,

I've looked for this everywhere but couldn't find an answer

I installed UNR on my Acer Aspire One netbook. It did not work the first time, so I installed it again. This time I partitioned my hard drive so that I would save my files in the second partition to keep them safe from system failures.

The partition mounts ok, but I can not read or write anything on it. there is one folder with a wierd name in it. I've tried deleting and recreating the partition many times but it has not worked.

EX3 file system, Primary, size 67GB, mounts into /media/disk

---

### Post by ptn107 on 2009-07-25
Post the output of:
```
ls -l /media/ && sudo fdisk -l
```

---

### Post by Atro on 2009-07-25
here it is

[PHP]

total 8
lrwxrwxrwx 1 root root    6 2009-07-25 12:16 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-07-25 12:16 cdrom0
drwxr-xr-x 3 root root 4096 2009-07-25 16:43 disk

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b5dad98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2           14224       14593     2972025    5  Extended
/dev/sda3            6080       14223    65416680   83  Linux
/dev/sda5           14224       14593     2971993+  82  Linux swap / Solaris

Partition table entries are not in disk order


[/PHP]

---

### Post by merlinus on 2009-07-25
I assume sda3 is the partition in question?  What mountpoint did you select for it?  You can look in /etc/fstab for this info.

---

### Post by Atro on 2009-07-25
Thats the problem I think, I didn't choose a mount location when I partitioned my disk, because I just didn't know what to select

here is the fstab content

```


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d05e5ef1-e8ba-442b-8e38-d280ff7b36c8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2937e786-a6c2-4c2c-b94a-5bfa46b2d167 none            swap    sw              0       0


```

---

### Post by merlinus on 2009-07-25
Create a mountpoint.  For example
```

sudo mkdir /media/sda3
```Then add this to the end of /etc/fstab

/dev/sda3 /media/sda3 ext3 relatime 0 1

assuming sda3 is formatted as ext3

and restart.

---

### Post by ptn107 on 2009-07-26
If you're just using /media/disk as storage then a quick fix is:
```
sudo chown -R $USER.$USER /media/disk
```

---

### Post by merlinus on 2009-07-26
IIRC, the command uses a : and not a .

sudo chown -R username:username /media/disk

---

### Post by ptn107 on 2009-07-26
. works as well

---

