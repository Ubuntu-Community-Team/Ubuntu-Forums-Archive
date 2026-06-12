---
title: "hardrive at /dev/sda unrecognized"
date: 2010-02-19
forum: General Help
---

### Post by rev9ers on 2010-02-19
Hello all,

As things go, both my laptop and desktop have gone belly up simultaneously. This question arises because my desktop will not boot. I can boot using the Ubuntu 9.10 livecd, which is how I am asking this question... Based on other threads I have found, please find below the output of some commands.

I fear that the hard drive may be dead. Please help.

The basic problem is that Ubuntu does not recognize the physical hard drive on which my boot partition resides. Using Palimpsest, the "ATA WDC ROM MODEL--SABRE--" is unrecognized, and SMART is not available on /dev/sda.

Here's the output of the following commands: 
sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
sudo fsck -V /dev/sda
sudo gparted
sudo parted /dev/sda

> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386583+  ee  GPT
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="HDD2" UUID="300c2f3f-3e46-499e-b140-738513fae5b0" TYPE="ext3" 
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/HDD2 type ext3 (rw,nosuid,nodev,uhelper=devkit)
ubuntu@ubuntu:~$ sudo fsck -V /dev/sda
fsck from util-linux-ng 2.16
[/sbin/fsck.ext2 (1) -- /dev/sda] fsck.ext2 /dev/sda 
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
Input/output error during read on /dev/sda

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.8.8.1.159-1e0e
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) p                                                                
Error: /dev/sda: unrecognised disk label                                  
(parted)                                                                  


and here's (or attached) a screenshot with Palimpsest running and showing the unrecognized hard drive:

---

