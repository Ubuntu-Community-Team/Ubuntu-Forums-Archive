---
title: "help with /etc/fstab"
date: 2009-11-29
forum: General Help
---

### Post by Engromada on 2009-11-29
i set a drive to mount automatically in fstab with the line:

/dev/sda6 /media/TEHSTORAGE auto rw,user,auto,exec 0 1

it's partition 6 on my first hard disk, and it's format is fat32.

the issue is that it mounts as read-only despite the rw option.

anyone know what's causing this?

---

### Post by sisco311 on 2009-11-29
[thread=283131]How to fstab[/thread]

Ownership and permissions of vfat / ntfs are set at the time of mounting.

i.e. to allow users in the plugdev group to read and write to the partitions:
```
/dev/sda6 /media/TEHSTORAGE auto defaults,gid=plugdev,dmask=002,fmask=113 0 2
```

---

