---
title: "LVM &amp; fstab"
date: 2011-10-15
forum: General Help
---

### Post by kentish on 2011-10-15
Hello 

Can anyone shed some light on how LVM should be mounted in fstab. I'm currently using dev/mapper/{logical volume name} and wonder if i should be using the UUID as recommended in Fstab or by device mapper as I'm currently doing?

I have the following groups and logical volumes

Volume Group        Logical Volumes
Data                      Music, Photos, Data
Media                    Videos
heavens-feather     Root, Swap_1

```

FStab
  GNU nano 2.2.6                      File: /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid                 0       0
/dev/mapper/heavens--feather-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=8163925d-c043-4820-b8a7-b9cbf925103d /boot ext2    defaults            0       2
/dev/mapper/heavens--feather-swap_1         none    swap   sw                  0       0
# LVM New
/dev/mapper/Media-Video /shared/videos  xfs     defaults                    0       1
/dev/mapper/Data-Music  /shared/music   ext4    defaults                    0       1
/dev/mapper/Data-Photos /shared/photos  ext4    defaults                    0       1
/dev/mapper/Data-Data   /shared/data    ext4    defaults                    0       1
```
Any suggestion or comments would be appreciated. 

BTW I'm running a headless Ubuntu 11.04 Server 

Thanks

---

### Post by redmk2 on 2011-10-15
> **kentish said:**
> Hello 

Can anyone shed some light on how LVM should be mounted in fstab. I'm currently using dev/mapper/{logical volume name} and wonder if i should be using the UUID as recommended in Fstab or by device mapper as I'm currently doing?

I have the following groups and logical volumes

Volume Group        Logical Volumes
Data                      Music, Photos, Data
Media                    Videos
heavens-feather     Root, Swap_1

```

FStab
  GNU nano 2.2.6                      File: /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid                 0       0
/dev/mapper/heavens--feather-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=8163925d-c043-4820-b8a7-b9cbf925103d /boot ext2    defaults            0       2
/dev/mapper/heavens--feather-swap_1         none    swap   sw                  0       0
# LVM New
/dev/mapper/Media-Video /shared/videos  xfs     defaults                    0       1
/dev/mapper/Data-Music  /shared/music   ext4    defaults                    0       1
/dev/mapper/Data-Photos /shared/photos  ext4    defaults                    0       1
/dev/mapper/Data-Data   /shared/data    ext4    defaults                    0       1
```
Any suggestion or comments would be appreciated. 

BTW I'm running a headless Ubuntu 11.04 Server 

Thanks

I mount my LVM partition just as you do.

There is a LVM bug when creating snapshots (creates duplicate UUID's).  That's why I use /dev to mount my LVM partitions.

Google with these keywords: lvm snapshot uuid bug

---

### Post by kentish on 2011-10-15
Cheers for that. I'll leave the fstab alone and have a google on the bug.

Thanks

---

