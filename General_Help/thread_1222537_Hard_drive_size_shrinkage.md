---
title: "Hard drive size shrinkage"
date: 2009-07-25
forum: General Help
---

### Post by Alan Zhao on 2009-07-25
Hi all,

Please help,

The following is the result of **fdisk -l** of one of the hard drives on my Ubuntu 8.04 server:

```

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa14a6e1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326   83  Linux

```Clearly you can see the drive has 82.3 GB of spaces, it's partitioned using **fdisk**. However the result of **df -h** gave me this:

```

/dev/sdb1              99M  5.6M   89M   6% /home/storage

```which now only has 99M of spaces.

This is the command I use to mount the drive in **/etc/fstab**:

```
/dev/sdb1     /home/storage     ext3    defaults        0       2
```What's the problem here?

Thanks in advance.

---

### Post by Alan Zhao on 2009-07-25
anybody?

---

### Post by DaithiF on 2009-07-26
This is a little unusual -- sounds like the filesystem is not sized correctly for the partition it is on.  Are you able to copy off the data somewhere safe and reformat the partition / recreate its filesystem (using gparted, for example?)  

If you can't do this then you can try the guide here:
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

to resize the filesystem on the fly.

good luck

---

### Post by drs305 on 2009-07-26
Note that the link is older and resize2fs works fine on ext3 and ext4 partitions now.

---

