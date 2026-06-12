---
title: "Read-only pendrive"
date: 2012-03-19
forum: General Help
---

### Post by Subidubi32 on 2012-03-19
I have a maxell pendrive, and if I use it on Ubuntu, Icannot write on it. Its not a permission problem, I tried sudo nautilus, but it diidn't help still said it's read-only. The problem is that it's have two partitions, a secure, and the storage. I don't use any password, but the secure partition contains an exe, where you can set up a password. I think there is the problem. Reading is fine. On windows no such problems. Thanks for the help.:-)

---

### Post by Subidubi32 on 2012-03-19
I also tried to open the exe with wine.

---

### Post by Subidubi32 on 2012-03-19
If I try to set it 'read and write' it says: The permissions could not be changed. Sorry, could not change the permissions of "2011-06-24 20.13.56.jpg": Error setting permissions: Read-only file system

---

### Post by varunendra on 2012-03-21
While it is plugged in, run and post the outputs of:
```
mount
sudo fdisk -l
```

If you don't care about that 'security' software, you may try to reformat it with gparted or in windows.

---

### Post by Subidubi32 on 2012-03-21
Mount:

/dev/sda7 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/szeplaki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=szeplaki)
/dev/sdc1 on /media/SECURE type vfat (ro,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdb1 on /media/BENCE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

---

### Post by Subidubi32 on 2012-03-21
fdisk -l:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba346776

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300674990   150337464    7  HPFS/NTFS/exFAT
/dev/sda2       300675070   398295039    48809985    5  Extended
/dev/sda5       394106880   398295039     2094080   82  Linux swap / Solaris
/dev/sda6       389916672   394106879     2095104   82  Linux swap / Solaris
/dev/sda7       300675072   385724415    42524672   83  Linux
/dev/sda8       385726464   389914623     2094080   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3951 MB, 3951034368 bytes
5 heads, 32 sectors/track, 48230 cylinders, total 7716864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd838fc90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8064     7716863     3854400    b  W95 FAT32

Disk /dev/sdc: 2 MB, 2097152 bytes
2 heads, 32 sectors/track, 64 cylinders, total 4096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32        4095        2032    1  FAT12

---

### Post by Subidubi32 on 2012-03-21
I'm naot sure, but I think i tried to format it with Gparted arount October, since it is a problem for a long time ago, But I will give it a try once again.

---

### Post by Subidubi32 on 2012-03-21
I formatted the whole pendrive, but the secure partition is not just a partition, it's another flashdisk. I could't apply the format operation, because it was read-only even for the Gparted LiveCD. But the storage area wasn't, so I farmatted it, and now Ubuntu can use it too, not just the windows... I don't know what happened, the filesystem is the same as before, but thank you for the help, it is solved! :)

---

