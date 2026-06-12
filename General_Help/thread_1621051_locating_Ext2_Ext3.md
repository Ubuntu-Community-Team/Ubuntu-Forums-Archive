---
title: "locating Ext2 Ext3"
date: 2010-11-13
forum: General Help
---

### Post by Konbuntu on 2010-11-13
how can i locate an Ext2 or Ext3 file system by using the terminal?

---

### Post by oldfred on 2010-11-13
Not sure what you mean by locate:

sudo fdisk -l

sudo blkid

Or do you want to mount it so you can use it?

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l


or permanently mount it:
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

# modify fstab to mount directory
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a
# mounted list
df -h
# or
sudo ls -ld /media/*
ls -l /dev/disk/by-uuid
ls /dev/disk/by-label -lah

---

### Post by nothingspecial on 2010-11-13
> **Konbuntu said:**
> how can i locate an Ext2 or Ext3 file system by using the terminal?

As long as they are mounted

```
mount | grep ext
```

---

