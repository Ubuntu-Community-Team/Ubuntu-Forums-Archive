---
title: "help with mint.."
date: 2010-02-19
forum: General Help
---

### Post by rahilm on 2010-02-19
I know this might not be the place to ask such questions...but i don't want to create another account on mint forums.. also mint is almost like ubuntu
the problem is only encountered in linux mint 8..and not in any other mint or ubuntu distro ..


when i try to edit partitions in Live-Cd via gparted to  install Mint, it gives error that```
Please unmount any logical partitions having a number higher than 6
```

there is no partition mounted, but wait.. sda7 is mounted nowhere and when i try to unmount it...error is :
```

umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```
which gives rise to another problem.. /dev/sda7 is automatically mounted on /isodevice... a new folder for me.. and i can't unmount it..

sudo fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5d41

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2944    23647648+   7  HPFS/NTFS
/dev/sda2            2945        7121    33551752+   7  HPFS/NTFS
/dev/sda3            7122       19457    99088920    f  W95 Ext'd (LBA)
/dev/sda5            7122        8426    10482348   83  Linux
/dev/sda6            8427        9618     9574708   83  Linux
/dev/sda7            9733       19457    78114816    7  HPFS/NTFS
/dev/sda8            9619        9732      915673+  82  Linux swap / Solaris

Partition table entries are not in disk order

```


any help is appreciated..

---

### Post by rahilm on 2010-02-19
i forgot mtab: (fstab is quite OK)
```

aufs / aufs rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev tmpfs rw,mode=0755 0 0
/dev/sda7 /isodevice fuseblk rw 0 0
/dev/loop0 /cdrom iso9660 rw 0 0
/dev/loop1 /rofs squashfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/mint/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=mint 0 0
/dev/sdb1 /media/06ede2a1-a63b-4605-ab12-93e95e6e82a8 ext2 rw,nosuid,nodev,uhelper=devkit 0 0
/dev/sdb2 /media/6C80-8A4D vfat rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush 0 0
```

I am using grub2 to boot an iso on my usb disk which is sdb..

as u can see there is a line over there 
/dev/sda7 /isodevice fuseblk rw 0 0

---

### Post by rahilm on 2010-02-20
Never mind.. i figured it out..
marking thread as solved

---

### Post by mcarni on 2010-04-09
hi Rahilm,

could you help me out, i have the same problem, but i don't see the solution....

Thanks

m

---

### Post by rahilm on 2010-04-09
Apparently, if you are mounting an iso via grub2. The partition containing the iso also gets mounted...in /isodevice.
So if you want to partition that drive. I would recommend move your iso file to the first partition or an external device

---

### Post by mcarni on 2010-04-09
Thanks Rahilm


i will stick the iso on an usb stick....

thanks

M

> **rahilm said:**
> Apparently, if you are mounting an iso via grub2. The partition containing the iso also gets mounted...in /isodevice.
So if you want to partition that drive. I would recommend move your iso file to the first partition or an external device

---

