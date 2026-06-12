---
title: "Unable to use chmod inside an external drive"
date: 2011-01-08
forum: General Help
---

### Post by MichaelPalin on 2011-01-08
I have recently installed Ubuntu 10.10 (x64) and I have noticed that I cannot change the permissions of any of the files on my external drives. If I do it from the Properties of the file by manually changing a field on permissions, it changes back automatically before my eyes. If I change it with chmod, nothing happens. They are all in "-rw-/drwx/-rwx------" mode. What should I do?

Thanks in advance.

---

### Post by Joe of loath on 2011-01-08
What filesystem is the drive?

---

### Post by ajgreeny on 2011-01-08
If the external drive is formatted as fat32, you can not do anything.

Fat32 file systems, to which most external drives are formatted at purchase, and other windows file systems, don't recognise linux permissions, so you are wasting your time.  All you can do is make sure that the mountpoint folder is set to be read/write, which it should be by default if the disk is automounted, but may need to be set in fstab if you use that method of mounting the disk.

If it is important for you to get specific permissions on those files you will need to reformat the disk as ext* or one of the other linux file systems.

---

### Post by MichaelPalin on 2011-01-08
According to the disk utility of Ubuntu, all of my external devices (two hard drives and one pendrive) are NTFS, :/

---

### Post by DeFrancoj on 2011-01-08
post output of mount and lsusb

---

### Post by MichaelPalin on 2011-01-08
mount results in:

```
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michaelpalin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michaelpalin)
/dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdb1 on /media/Iomega HDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/My Passport type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

and lsusb:

```
Bus 007 Device 002: ID 0e8f:0003 GreenAsia Inc. MaxFire Blaze2
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c31a Logitech, Inc. 
Bus 006 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 059b:0470 Iomega Corp. Prestige Portable Hard Drive
Bus 002 Device 002: ID 1058:070a Western Digital Technologies, Inc. My Passport Essential SE
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by DeFrancoj on 2011-01-09
Yeah I don't think that the POSIX file permissions are a part of NTFS, which means you'd have to use ACLs or something if you really wanted fine control over permissions on your external drive.

---

