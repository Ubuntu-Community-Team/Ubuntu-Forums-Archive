---
title: "disk partition mount"
date: 2011-01-17
forum: General Help
---

### Post by L Style on 2011-01-17
I have 10gb partition, now I can't mount this partition, when i tried to mount this partition this message displayed.

Unable to mount location

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 2 in /etc/fstab is bad
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab



please guys help me. how to fix this. this partition got my important files. please help me

---

### Post by L Style on 2011-01-17
bump

---

### Post by Elfy on 2011-01-17
post results of these from a terminal

```
cat /etc/fstab
sudo fdisk -l
sudo blkid
mount
```

Do not bump so soon.

---

### Post by L Style on 2011-01-17
> **forestpiskie said:**
> post results of these from a terminal

```
cat /etc/fstab
sudo fdisk -l
sudo blkid
mount
```

Do not bump so soon.

lachitha@lachitha-desktop:~$ cat /etc/fstab
UUID=cca47391-3cbb-4525-a17a-6838db02a25c / ext4 defaults 0 1
UUID=C229-3FF5 /media/MEDIA & FIL vfat defaults 0 0
UUID=dcb8af82-0ac2-41f0-8744-819c440b57fe swap swap sw 0 0
lachitha@lachitha-desktop:~$ sudo fdisk -l
[sudo] password for lachitha: 

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44121ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1203     9663066   83  Linux
/dev/sda2            1204        4997    30474915+   f  W95 Ext'd (LBA)
/dev/sda5            1251        2563    10546641    b  W95 FAT32
/dev/sda6            2564        3876    10546641    b  W95 FAT32
/dev/sda7            3877        4997     9004401    b  W95 FAT32
/dev/sda8            1204        1250      376832   82  Linux swap / Solaris

Partition table entries are not in disk order

Sda5 is the partition not mounted

---

### Post by L Style on 2011-01-17
> **forestpiskie said:**
> post results of these from a terminal

```
cat /etc/fstab
sudo fdisk -l
sudo blkid
mount
```

Do not bump so soon.

lachitha@lachitha-desktop:~$ cat /etc/fstab
UUID=cca47391-3cbb-4525-a17a-6838db02a25c / ext4 defaults 0 1
UUID=C229-3FF5 /media/MEDIA & FIL vfat defaults 0 0
UUID=dcb8af82-0ac2-41f0-8744-819c440b57fe swap swap sw 0 0
lachitha@lachitha-desktop:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44121ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1203     9663066   83  Linux
/dev/sda2            1204        4997    30474915+   f  W95 Ext'd (LBA)
/dev/sda5            1251        2563    10546641    b  W95 FAT32
/dev/sda6            2564        3876    10546641    b  W95 FAT32
/dev/sda7            3877        4997     9004401    b  W95 FAT32
/dev/sda8            1204        1250      376832   82  Linux swap / Solaris

Partition table entries are not in disk order
lachitha@lachitha-desktop:~$ sudo blkid
/dev/sda1: UUID="cca47391-3cbb-4525-a17a-6838db02a25c" TYPE="ext4" 
/dev/sda5: LABEL="MEDIA & FIL" UUID="C229-3FF5" TYPE="vfat" 
/dev/sda6: LABEL="STUFF" UUID="3C1A-29BD" TYPE="vfat" 
/dev/sda7: LABEL="MUSIC" UUID="F887-6172" TYPE="vfat" 
/dev/sda8: UUID="dcb8af82-0ac2-41f0-8744-819c440b57fe" TYPE="swap" 
lachitha@lachitha-desktop:~$ mount
/dev/sda1 on / type ext4 (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lachitha/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lachitha)
/dev/sda5 on /media/MEDIA type vfat (rw)
/dev/sr2 on /media/Mobile Partner type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
lachitha@lachitha-desktop:~$

---

### Post by Elfy on 2011-01-17
Try 



```
UUID=C229-3FF5 /media/MEDIA & FIL vfat defaults,user,dmask=027,fmask=137 0 0
```

```
gksu gedit /etc/fstab
```

```

sudo umount /media/MEDIA
sudo mount -a
```

---

### Post by L Style on 2011-01-17
> **forestpiskie said:**
> Try 



```
UUID=C229-3FF5 /media/MEDIA & FIL vfat defaults,user,dmask=027,fmask=137 0 0
```

```
gksu gedit /etc/fstab
```

```

sudo umount /media/MEDIA
sudo mount -a
```

Lot of thanks, Its work now.:P:P:P:P:P

---

