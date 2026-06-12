---
title: "Installing Lubuntu"
date: 2010-11-10
forum: General Help
---

### Post by Hippytaff on 2010-11-10
I'm installing lubuntu on an old lap top, dual boot with xp. For some reason the install doesn't see the xp. Doesn't think there is an os installed. got this

```

Filesystem            Size  Used Avail Use% Mounted on
aufs                  249M   23M  226M  10% /
none                  242M  248K  242M   1% /dev
/dev/sr0              521M  521M     0 100% /cdrom
/dev/loop0            502M  502M     0 100% /rofs
none                  249M     0  249M   0% /dev/shm
tmpfs                 249M  132K  249M   1% /tmp
none                  249M   76K  249M   1% /var/run
none                  249M  4.0K  249M   1% /var/lock
none                  249M     0  249M   0% /lib/init/rw

``````

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xac3aa428

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2431    19526976    7  HPFS/NTFS
/dev/sda2            2432        2432        8032+   f  W95 Ext'd (LBA)

``````

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)

```Any ideas...don't want to start installing stuff on the wifes laptop if it doesn't see xp. Could go horribly wrong, including me having to find somewhere else to sleep :-)

---

### Post by cavalier911 on 2010-11-10
It doesn't look like you have any room to install Lubuntu.
/dev/sda1 holding winxp take's up all of /dev/sda
When I installed Lubuntu I wanted to use ext3 and legacy grub.
It's very unfriendly when you need to customize your install.
By default when the  installer see's no empty space it wants to wipeout whatever is there.
How much empty space is there on /dev/sda1 ?
Don't shrink /dev/sda1 without first backing it up to an external hard drive!
You'd have to shrink /dev/sda1 to make room for new expanded /dev/sda2 to hold Lubuntu.
If this was not my own computer I'd leave it alone. [-X

---

### Post by Hippytaff on 2010-11-11
Cheers, I'll either let it clunk along with xp, or persuade the wife that lubuntu is a better os than xp and wipe it.
 
That had me baffled :-)

---

