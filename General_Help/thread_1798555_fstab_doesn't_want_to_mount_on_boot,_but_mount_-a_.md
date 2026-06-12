---
title: "fstab doesn't want to mount on boot, but mount -a works"
date: 2011-07-06
forum: General Help
---

### Post by kyutums on 2011-07-06
I'm using Ubuntu 10.10 - 2.6.35-30-generic.

I added a hard drive to my current single hard drive machine. I already made 2 partitions using GParted, both having ext4 fs. I tried to automount the 2 partitions by using the following /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4ebcd466-57a4-4c3d-9c1a-573a968b9b55 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8638e73a-064e-4ce0-832c-af3bafa179cf none            swap    sw              0       0

/dev/sdc1 /media/BackupMain ext4 rw,nosuid,nodev,uhelper=udisks 0 2
/dev/sdc2 /media/SharedFiles ext4 rw,nosuid,nodev,uhelper=udisks 0 2
```

When I rebooted the machine, I received the "Press S to skip mount or M for manual recovery" message. I pressed S to skip mount. When I was now logged in, I tried "sudo mount -a" and it mounted the aforementioned hard drives.

Did I miss something in my fstab?

---

### Post by drs305 on 2011-07-06
You might try adding either "defaults" or "auto" to the options. The former includes 'auto' as a mounting option, while the second will allow the partition(s) to mount automatically if you don't want to include 'defaults' as an option.

---

### Post by kyutums on 2011-07-17
Adding auto by changing the lines into
> /dev/sdc1 /media/BackupMain ext4 auto,rw,nosuid,nodev,uhelper=udisks 0 2
/dev/sdc2 /media/SharedFiles ext4 auto,rw,nosuid,nodev,uhelper=udisks 0 2
didn't work (which I find to be quite weird).

I had to install pysdm to make it work. :)

---

