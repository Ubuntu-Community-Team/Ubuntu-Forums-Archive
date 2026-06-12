---
title: "Swap unable to mount"
date: 2009-12-10
forum: General Help
---

### Post by solidjoe on 2009-12-10
Recently I started having an error on startup, saying that the swap partition in /etc/fstab is not ready to mount. It pauses then starts up as normal. Xubuntu isn't my speciality, but it looks like fstab has become corrupted. This is a dual boot system with Xubuntu 9.10 and Windows XP on it, Linux is the main OS and the boot loader. Gparted seems unable to display the partitions, even using the latest live cd. Just shows one large unallocated partition, which obviously, is incorrect. Both Linux and Windows appear to work correctly. Windows can see all the partitions.

fdisk -l output:

```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3124abc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        7296    39070080    5  Extended
/dev/sda3   *        2798        6621    30716280    7  HPFS/NTFS
/dev/sda5            2433        2795     2915766   82  Linux swap / Solaris

```cat /etc/fstab output:

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
UUID=b61d7bd7-f038-4dd4-9cf8-6298442ef83b /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6a698d98-d4b5-470c-ad1f-f0f5f59b4235 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Suggestions?

---

### Post by lmarmisa on 2009-12-10
I think that it is a problem with the UUID of the swap partition.

Type this command:

**sudo blkid**

and update the **/etc/fstab** file with the correct UUID of the swap partition.

Anoter option is to modify the long swap UUID string with /dev/sda5 in fstab:

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
UUID=b61d7bd7-f038-4dd4-9cf8-6298442ef83b /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```Best regards,

Luis

---

### Post by solidjoe on 2009-12-10
Seems like it lost its UUID. I just replaced it in /etc/fstab with /dev/sda5 and it seems to have corrected the problem. Gparted still thinks the whole disk is one unallocated partition, no idea why. Something with the boot record maybe? Or a corrupted partition somewhere. In any event, this isn't a production machine, so I'm not entirely concerned about it. Thanks!

---

### Post by hal10000 on 2009-12-10
There seems to be something terribly wrong with your partitioning at all.
According to your listing of the fdisk -l command, your NTFS partition resides on a logical partition inside your extended partition. But if this is true, then it could not be named as /dev/sda3, it must be /dev/sda5 or /dev/sda6, because in linux a logical partition must be named /dev/sda5, /dev/sda6, /dev/sda7 etc.
/dev/sda1 ..... /dev/sda4 are only for primary partitions.

I guess the fdisk command is able to correct this, but be careful, fdisk is not very user friendly.

---

