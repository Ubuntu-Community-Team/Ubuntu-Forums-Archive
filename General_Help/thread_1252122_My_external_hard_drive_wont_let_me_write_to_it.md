---
title: "My external hard drive wont let me write to it"
date: 2009-08-28
forum: General Help
---

### Post by bobyo134 on 2009-08-28
I have recently purchased a new server ,(running Debian 4.0) i hav it setup as a web server and it runs great , so i begain setting it up as a file server with the help of my freind who can do that in his sleep, but we came into a snag when my external hard drive mounts as a "read only disk" , i can access all the files fine but i am not able to add/change . It was a NTFS file system , so i put it on my windows pc , and formatted it for fat32 , same problem after re-connecting to server , i need help plz !!!!

---

### Post by dannyboy79 on 2009-08-28
> **bobyo134 said:**
> I have recently purchased a new server ,(running Debian 4.0) i hav it setup as a web server and it runs great , so i begain setting it up as a file server with the help of my freind who can do that in his sleep, but we came into a snag when my external hard drive mounts as a "read only disk" , i can access all the files fine but i am not able to add/change . It was a NTFS file system , so i put it on my windows pc , and formatted it for fat32 , same problem after re-connecting to server , i need help plz !!!!
please inform us of the mount options you're using to mount it? if you plug it in, what does issuing these commands at the command line output?

```
sudo fdisk -l
```


```
mount
```



```
tail -20 /var/log/syslog
```

are you using fstab to mount it or are you just counting on HAL to see it and mount it for you? once you post back output from above commands maybe someone can help you.

---

### Post by bobyo134 on 2009-08-28
HP-dl380-1:/home/bob# sudo fdisk -l

Disk /dev/cciss/c0d0: 36.7 GB, 36765696000 bytes
255 heads, 63 sectors/track, 4469 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

          Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *           1        4280    34379068+  83  Linux
/dev/cciss/c0d0p2            4281        4469     1518142+   5  Extended
/dev/cciss/c0d0p5            4281        4469     1518111   82  Linux
swap / Sol aris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32



mount
/dev/cciss/c0d0p1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
/dev/sdb1 on /media/FILE-DRIVE2 type vfat
(rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)


tail -20 /var/log/syslog

Aug 28 12:53:03 HP-dl380-1 kernel: sdb1: rw=0, want=99560841700, limit=976768002
Aug 28 12:53:05 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:05 HP-dl380-1 kernel:     invalid access to FAT (entry 0x318258f9)
Aug 28 12:53:06 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:06 HP-dl380-1 kernel:     invalid access to FAT (entry 0xbd988d00)
Aug 28 12:53:06 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:06 HP-dl380-1 kernel:     invalid access to FAT (entry 0x20016498)
Aug 28 12:53:06 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:06 HP-dl380-1 kernel:     invalid access to FAT (entry 0xa84fde54)
Aug 28 12:53:07 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:07 HP-dl380-1 kernel:     invalid access to FAT (entry 0x72a3560a)
Aug 28 12:53:07 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:07 HP-dl380-1 kernel:     invalid access to FAT (entry 0x38dff3e7)
Aug 28 13:09:01 HP-dl380-1 /USR/SBIN/CRON[9325]: (root) CMD (  [ -d
/var/lib/php5 ] && find /var/lib/php5/ -type f -cmin
+$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug 28 13:17:01 HP-dl380-1 /USR/SBIN/CRON[9434]: (root) CMD (   cd /
&& run-parts --report /etc/cron.hourly)
Aug 28 13:31:01 HP-dl380-1 -- MARK --
Aug 28 13:33:01 HP-dl380-1 /USR/SBIN/CRON[9659]: (nobody) CMD ([ -x
/usr/share/sa-exim/greylistclean ] &&
/usr/share/sa-exim/greylistclean)
Aug 28 13:33:02 HP-dl380-1 sa-exim[9660]: Removed 0 of 0 greylist
tuplets in 0 seconds
Aug 28 13:33:02 HP-dl380-1 sa-exim[9660]: Removed 0 of 0 greylist
directories in 0 seconds
Aug 28 13:39:01 HP-dl380-1 /USR/SBIN/CRON[9774]: (root) CMD (  [ -d
/var/lib/php5 ] && find /var/lib/php5/ -type f -cmin
+$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

---

### Post by dannyboy79 on 2009-08-28
> **bobyo134 said:**
> HP-dl380-1:/home/bob# sudo fdisk -l

Disk /dev/cciss/c0d0: 36.7 GB, 36765696000 bytes
255 heads, 63 sectors/track, 4469 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

          Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *           1        4280    34379068+  83  Linux
/dev/cciss/c0d0p2            4281        4469     1518142+   5  Extended
/dev/cciss/c0d0p5            4281        4469     1518111   82  Linux
swap / Sol aris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32



mount
/dev/cciss/c0d0p1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
/dev/sdb1 on /media/FILE-DRIVE2 type vfat
(rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)


tail -20 /var/log/syslog

Aug 28 12:53:03 HP-dl380-1 kernel: sdb1: rw=0, want=99560841700, limit=976768002
Aug 28 12:53:05 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:05 HP-dl380-1 kernel:     invalid access to FAT (entry 0x318258f9)
Aug 28 12:53:06 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:06 HP-dl380-1 kernel:     invalid access to FAT (entry 0xbd988d00)
Aug 28 12:53:06 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:06 HP-dl380-1 kernel:     invalid access to FAT (entry 0x20016498)
Aug 28 12:53:06 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:06 HP-dl380-1 kernel:     invalid access to FAT (entry 0xa84fde54)
Aug 28 12:53:07 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:07 HP-dl380-1 kernel:     invalid access to FAT (entry 0x72a3560a)
Aug 28 12:53:07 HP-dl380-1 kernel: FAT: Filesystem panic (dev sdb1)
Aug 28 12:53:07 HP-dl380-1 kernel:     invalid access to FAT (entry 0x38dff3e7)
Aug 28 13:09:01 HP-dl380-1 /USR/SBIN/CRON[9325]: (root) CMD (  [ -d
/var/lib/php5 ] && find /var/lib/php5/ -type f -cmin
+$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Aug 28 13:17:01 HP-dl380-1 /USR/SBIN/CRON[9434]: (root) CMD (   cd /
&& run-parts --report /etc/cron.hourly)
Aug 28 13:31:01 HP-dl380-1 -- MARK --
Aug 28 13:33:01 HP-dl380-1 /USR/SBIN/CRON[9659]: (nobody) CMD ([ -x
/usr/share/sa-exim/greylistclean ] &&
/usr/share/sa-exim/greylistclean)
Aug 28 13:33:02 HP-dl380-1 sa-exim[9660]: Removed 0 of 0 greylist
tuplets in 0 seconds
Aug 28 13:33:02 HP-dl380-1 sa-exim[9660]: Removed 0 of 0 greylist
directories in 0 seconds
Aug 28 13:39:01 HP-dl380-1 /USR/SBIN/CRON[9774]: (root) CMD (  [ -d
/var/lib/php5 ] && find /var/lib/php5/ -type f -cmin
+$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)

what are the permissions on the /media/FILE-DRIVE2 folder before you mount it? here is what my fstab entry looks like for my fat32 drive.

```
UUID=81B8-2F2C  /media/fat32    vfat    utf8,umask=000,gid=1000,uid=1000 0       1

```

you still didn't answer my question about how your mounting it? via fstab or just using HAL?

it appears you might need to delete the fat32 partition and re-do it as the kernel is having trouble with it according to that log file. have you just tried formatting it with gparted?

---

