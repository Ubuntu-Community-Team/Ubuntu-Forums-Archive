---
title: "cdrom disappeared from places"
date: 2010-08-04
forum: General Help
---

### Post by potam on 2010-08-04
Hello all,

In one of our computers, running 10.04, the cdrom icon disappeared from Places menu (also not present in Computer).

Dmesg clearly shows, that drive is recognised, the block device exists, and the old fashion ```
mount -t iso9660 /dev/sr0 /media/cdrom
``` works. Also, the cd is not being automounted when inserted.

I tried everything I got in my mind, but no success. Even cleared all the gnome settings directories, to start from zero.

My fstab file looks like this:
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
UUID=4849e677-32a5-4ad5-a3e4-2cd217b5fd94 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=d1e3723b-42eb-43b0-b170-b3d9db5a6e19 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=d4f368ef-0ddf-4638-9ea4-940319a63fcc none            swap    sw              0       0

```

---

