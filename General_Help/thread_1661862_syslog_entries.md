---
title: "syslog entries"
date: 2011-01-07
forum: General Help
---

### Post by Robbyx on 2011-01-07
My syslog is showing a lot of entries like the following:

> Jan  7 14:31:44 rob kernel: [16833.807237] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:31:46 rob kernel: [16835.802062] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:31:46 rob kernel: [16835.948146] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:0a:01:3e:00:14:7f:25:9c:b7:08:00 SRC=213.155.157.51 DST=192.168.1.64 LEN=40 TOS=0x00 PREC=0x00 TTL=55 ID=0 DF PROTO=TCP SPT=80 DPT=53235 WINDOW=0 RES=0x00 RST URGP=0 
Jan  7 14:31:48 rob kernel: [16837.802907] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:31:50 rob kernel: [16839.803632] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:31:52 rob kernel: [16841.803435] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:31:54 rob kernel: [16843.803224] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:31:56 rob kernel: [16845.802011] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:31:58 rob kernel: [16847.802812] VFS: busy inodes on changed media or resized disk sr0
Jan  7 14:32:00 rob kernel: [16849.802602] VFS: busy inodes on changed media or resized disk sr0

I think I have messed up my media setup:

fstab:

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
UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=e36cb6cf-f372-4418-bd8b-f36a27dc3e76 none            swap    sw              0       0
# dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                  0  0  
# does not exist: UUID=724E07853D78E7A8                      /media/mydocs  ntfs         user,rw,auto,exec,nls=utf8,unmask=007  0  2  
# does not exist:
# does not exist:     UUID=f35c7bf9-9c2b-4ec9-9522-84d73f3c37db  /media/f       reiserfs     noatime,user,notail,rw                 0  0  
UUID=7b859c36-c68d-408f-9425-de9f525f3c71  /media/g       reiserfs     noatime,user,notail,rw                 0  0  
UUID=86290d05-e673-4310-9f3e-93af30cc13af  /media/video   reiserfs     noatime,user,notail,rw                 0  0  
# (does not exist) UUID=4A16-E85E /media/sda1 vfat 
#(does not exist)none                                       /proc/bus/usb  usbfs        devgid=126,devmode=664                 0  0  
# does not exist: /dev/sdc1                                  /media/mydocs    vfat         user,rw,noauto,exec,utf8                              0  0   
# localhost:/wuala /home/luzius/wuala/direct nfsdefaults,users,noauto,rsize=8192,wsize=8192,timeo=60,acregmin=10,noac,intr,nolock,soft
```

```
rob@rob:~$ sudo fdisk -lu
[sudo] password for rob: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    59842124    29921031   83  Linux
/dev/sda2        59842125   122849054    31503465   83  Linux
/dev/sda3       122849116   964815704   420983294+   5  Extended
/dev/sda4       964815705   976768064     5976180   82  Linux swap / Solaris
/dev/sda5       122849118   337364999   107257941   83  Linux
/dev/sda6       337365063   964815704   313725321   83  Linux

Disk /dev/sdb: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3aa5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     4014079     2007024    e  W95 FAT16 (LBA)

Disk /dev/sdc: 250.1 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001   fd  Linux RAID autodetect
rob@rob:~$ 

```

```
rob@rob:~$ sudo blkid
/dev/sda1: UUID="4a60ff9d-f704-4d04-a829-4c4702f5c203" TYPE="ext3" 
/dev/sda2: UUID="45a2e92c-c759-4732-9662-988da7f8ea7b" TYPE="ext3" 
/dev/sda4: UUID="e36cb6cf-f372-4418-bd8b-f36a27dc3e76" TYPE="swap" 
/dev/sda5: UUID="7b859c36-c68d-408f-9425-de9f525f3c71" TYPE="reiserfs" 
/dev/sda6: UUID="86290d05-e673-4310-9f3e-93af30cc13af" TYPE="reiserfs" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="KINGSTON" UUID="B72D-6759" TYPE="vfat" 
/dev/sdc1: LABEL="mydocs" UUID="724E07853D78E7A8" TYPE="ntfs" 

```

At the moment the panel disk mounter is showing that video and g are not mounted.

I have the following in media:

cdrom0
g
kingston
mydocs
video

**Can anyone tell me what I have done wrongly?**

Robin

---

### Post by QLee on 2011-01-07
[QUOTE=Robbyx]...
At the moment the panel disk mounter is showing that video and g are not mounted.

...[/QUOTE]

What do you mean by "panel disk mounter"?

What is the result of the command, mount?

---

### Post by Robbyx on 2011-01-07
> **QLee said:**
> What do you mean by "panel disk mounter"?

What is the result of the command, mount?

The panel disk mounter is the gnome panel widget that shows the disks/ partitions that are available for mounting.

```
rob@rob:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro,commit=0)
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
/dev/sda2 on /home type ext3 (rw,commit=0)
/dev/sdc1 on /media/mydocs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/g type reiserfs (rw,noexec,nosuid,nodev,noatime,notail)
/dev/sda6 on /media/video type reiserfs (rw,noexec,nosuid,nodev,noatime,notail)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=rob)
rob@rob:~$ 

```

---

### Post by QLee on 2011-01-08
The results of the mount command shows that "g" and "video" are mounted. Sorry, I have no experience with the disk mounter widget, I can't suggest any reason why it doesn't show them as mounted.

---

### Post by Robbyx on 2011-01-08
What I have found is a number of my media folders had owners other than me:

Video   1001
cdrom0   root
g        root

I have changed the owner to me. Do you know if the change is wise?

---

