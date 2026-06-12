---
title: "WD MyPassport not recocnized except as CD"
date: 2009-12-27
forum: General Help
---

### Post by jongudm on 2009-12-27
I just installed Ubuntu 9.10 on my work computer but the WD MyPassport I used to store my files for the transition is not recognized by Ubuntu as an hd drive, just as a CD ROM (there is a CD image on it with some auto backup software for Windows).  Output of lsusb is:

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 17ef:1003 Lenovo 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1058:070a Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 17ef:1004 Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```Output of sudo fdisk -l is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18726   150416563+  83  Linux
/dev/sda2           18727       19457     5871757+   5  Extended
/dev/sda5           18727       19457     5871726   82  Linux swap / Solaris
```Any ideas on how to get the disk mounted?

---

### Post by stuffystuff200681 on 2009-12-27
its likely that the files are not only software, but drivers.
would like to know how you get around to solve this...it is happening too often these days (phones, mp3 players, and now DISK DRIVES):(

the reason is probably that the software is the only thing that can unlock some algorithm on the REAL drive....Darn Apple for what they have done!!!!(or started)

oh yeah, and merry ubuntuing!!!:popcorn:

---

### Post by jongudm on 2009-12-31
I kept investigating over the last few days and am still stuck.  Here is the output of cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=566aa219-d80b-437b-afa6-8861fd73e7ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d6d5824a-dc07-40cb-b16d-30fdfe87764f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```Output of blkid:

```
/dev/sda1: UUID="566aa219-d80b-437b-afa6-8861fd73e7ba" TYPE="ext4" 
/dev/sda5: UUID="d6d5824a-dc07-40cb-b16d-30fdfe87764f" TYPE="swap" 
```Output of mount:

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/jongudm/.Private on /home/jongudm type ecryptfs (ecryptfs_sig=9c7367b18a266918,ecryptfs_fnek_sig=1c19f10754e968da,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/jongudm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jongudm)
/dev/sr1 on /media/WD SmartWare type udf (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,umask=0077)
```As I said at the start only the CD image on the drive is mounted and visible at all when I plug in the drive.  Presumably I can format the drive to make it appear properly but I have important data on there so that is clearly not my first choice...

---

### Post by jongudm on 2009-12-31
Just a little update, other usb drives are recognised and mounted automatically without any problems.

---

### Post by andreh8 on 2009-12-31
Hi,

what do you see in /var/log/messages when you plug in the device ?

(e.g. do

  tail -f /var/log/messages

then press a few times enter on this shell and then plug in the external harddisk)

best regards,

Andre

---

### Post by dcstar on 2009-12-31
> **jongudm said:**
> I just installed Ubuntu 9.10 on my work computer but the WD MyPassport I used to store my files for the transition is not recognized by Ubuntu as an hd drive, just as a CD ROM (**there is a CD image on it with some auto backup software for Windows**).
.......
Any ideas on how to get the disk mounted?

A lot of these things with prebuilt Windows software are actual CD images that auto-run in Windows systems and then load special Windows-only software to allow only Windows systems to use the storage.

You will probably have to copy this data off on a Windows system and then put it on a normal storage device so Linux can access it.

---

### Post by jongudm on 2010-01-03
> **andreh8 said:**
> Hi,

what do you see in /var/log/messages when you plug in the device ?

(e.g. do

  tail -f /var/log/messages

then press a few times enter on this shell and then plug in the external harddisk)

best regards,

Andre

Now I feel like an idiot...  I did what you suggested and when I saw the output I remembered that I secured the drive with a password! #-oI opened it on a Windows system, removed the password security and now it is mounted without any problems on the Ubuntu system!

Thanks for your help, everyone who posted or read!

---

