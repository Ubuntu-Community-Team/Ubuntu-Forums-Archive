---
title: "Cryptsetup with Luks seems to fail to unlock"
date: 2010-08-07
forum: General Help
---

### Post by ilon_s on 2010-08-07
Situation:
Reinstalled ubuntu and when i try to mount my old disks after using cryptsetup luksOpen i'm uname to mount the devices.
I did rearrange the disks inside of the computer after the reinstallation, added some new disks etc, but that shouldnt effect the crypto and LVM allready on it.
The LVM partitions are marked as ACTIVE aswell.

cryptsetup version is 1.1.0-rc2, tried with 1.0.6 from a Ubuntu 9.10 CD aswell.

Physical disk -> LVM2 group -> LVM2 partition -> crypto using Luks

i try to unlock it using:

```
# cryptsetup luksOpen /dev/mapper/group1-media media
Enter passphrase for /dev/mapper/group1-media: 
Key slot 0 unlocked.
root@Starshine:/# mount /dev/mapper/media /mnt/
mount: you must specify the filesystem type
```

dmesg and /var/log/messages comes up with nothing, nor does --verbose as argument to cryptsetup.

A scan with testdisk on the drive finds no valid partitions, and i'm certain that i have not overwritten anything during the reinstallation, i'm very carefully when doing changes to my disks due to some (for me) valuable information on it.

Any ideas would be appreciated, and no, i do NOT have an backup :(

Kind regards,
Ilon Sjögren

---

### Post by ilon_s on 2010-08-08
forgot, here's the fdisk -l for /dev/mapper/media:
```
fdisk -l /dev/mapper/media 

Disk /dev/mapper/media: 1160.1 GB, 1160059547648 bytes
255 heads, 63 sectors/track, 141035 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf960c21c

Disk /dev/mapper/media doesn't contain a valid partition table

```

---

