---
title: "Mounting partitions"
date: 2009-12-28
forum: General Help
---

### Post by Marvin666 on 2009-12-28
I created 3 folders in my /home directory, and I'm trying to use them as the mount point for 3 partitions. /home/Ntfs is the mount point for  /dev/sda3 (ntfs). /home/Linux is the mount point for a thumb drive (ext4) /dev/sdb1. /home/Universal is the mount point for the thumb drive (ntfs) /dev/sdc1. I know I have to edit my fstab, but I'm not sure what to put, or what directory it's in.

---

### Post by sisco311 on 2009-12-28
[thread=283131]How to fstab[/thread]


The fstab file is in the /etc directory:
```
gksu mousepad /etc/fstab
```

An entry looks like this:
```
UUID=<uuid of the partition>    /mount/point    type(ntfs or ext4)    mount-options    0     2
```

to get the UUID of the partition run:
```
sudo blkid -o udev /dev/sd**XY**
```

i.e.:
```
sudo blkid -o udev /dev/sda1 
ID_FS_LABEL=arch
ID_FS_LABEL_ENC=arch
ID_FS_UUID=**72d1e24a-1060-4a1f-95a0-182cab94844d**
ID_FS_UUID_ENC=72d1e24a-1060-4a1f-95a0-182cab94844d
ID_FS_TYPE=ext3

```

The default mount option for the ext4 partition is **relatime** and for the ntfs partitions: **defaults,gid=plugdev,dmask=0002,fmask=0113**

---

### Post by Marvin666 on 2009-12-28
I edited my fstab, and rebooted, but it doesn't seem to have worked. Now it gives me the error message "You are not not privileged to mount the volume "<label>".

---

### Post by sisco311 on 2009-12-29
Please post the output of:
```
mount
```
```
sudo blkid
```
and
```
cat /etc/fstab
```

---

