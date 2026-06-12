---
title: "/etc/fsdisk corrupted"
date: 2011-03-03
forum: General Help
---

### Post by sda123 on 2011-03-03
Please help cause one day i did cp /dev/sdb (Thats my memory stick) /etc/fstab now fstab is half block device half text file. I have a ubuntu live disk and a windows machine that is working. When I boot it up it fails to load and asks me for my root password. I try fsck but it says

WARNING: Unknown line 56723 on etc/fstab
WARNING: Unknown line 21975 on etc/fstab

You know things a bit like that
:x

---

### Post by dandnsmith on 2011-03-03
You need to boot from the liveCD and mount the partition of your HDD where your linux root filesystem is.
Then you can get to its /etc/fstab.

It's possible that if you delete the current fstab you might be able to get going, or you could try creating a new one.

The essential lines of mine look like:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=caa0888d-36f5-4073-80a4-6c37510b3ab9 /               ext3    errors=remount-ro 0       1

```

You'll have to change the UUID there for your own UUID, which you can get from the liveCD Ubuntu using the blkid hint at the start of my listing, and also the filesystem type (as you may not be using ext3).

HTH

---

### Post by seawolf167 on 2011-03-03
I'd try what dandnsmith suggested

Boot off a LiveCD, then create a new /etc/fstab file using his header information from the previous post.

To find your partitions info

```
sudo fdisk -l
```

to find the file system types and UUIDs

```
blkid
```

to see what is currently mounted

```
mount
```

See the fstab link in my signature for more info on editing that file

---

### Post by sda123 on 2011-03-04
Or if i press F12 when my laptop turns on, it gives me a choice of network boot, cd boot, memory stick boot or hard disk boot. If I choose Hard disk will it work?

---

### Post by sda123 on 2011-03-04
Thx I'm Just trying it out now

---

