---
title: "please help me finish creating raid1 ramdisk/hdd partition"
date: 2011-03-08
forum: General Help
---

### Post by Snoman314 on 2011-03-08
After some hours of googling, I've managed to increase the size of the default ramdisks (/dev/ram0-16) to 1 GiB each, I raided them together with mdadm to try it out, then created a filesyste, mounted it etc etc. No problems. The problem comes when I used gparted to move my windows partition over and in the unallocated space (1 GiB), I created an unformatted partition (/dev/sda2)

Now when I try to create the raid array I get the following:


```
:~$ sudo mdadm --create /dev/md0 -l 1 -n 2 /dev/ram0 /dev/sda2
mdadm: Cannot open /dev/sda2: Device or resource busy
mdadm: create aborted
```

I though to try removing the partition again and creating a new unformatted one, but gparted gives:

> Partition(s) 2 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.

Some potentially useful stuff:


```
:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1ea21ea1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6988    56125408+   7  HPFS/NTFS
/dev/sda3            7119        9730    20974592   83  Linux

:~$ cat /etc/mtab
/dev/sda3 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/james/.Private /home/james ecryptfs ecryptfs_sig=582c0fe164cb4c0a,ecryptfs_fnek_sig=38f311108c465ae5,ecryptfs_cipher=aes,ecryptfs_key_bytes=16 0 0
gvfs-fuse-daemon /home/james/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=james 0 0

```

Before anyone says it, yes I know I can use tmpfs, but this is obviously temporary.
What I'm trying to achieve is a raid 1 array, with one of the block devices being a ramdisk, the other a hdd partition. The idea being that on boot, the array gets rebuilt from the hdd into ram, and from there I get the speed of a ramdisk and the persistence of hdd.

Edit: By the way I've been up way longer than I intended, working on this. It's entirely possible I'm being stupid, but your help would be appreciated anyway.

---

### Post by Snoman314 on 2011-03-08
I thought I'd try something else to figure out what /dev/sda2 is up to. I tried rebooting and using gparted to format to ext3. I got the following error:

```
GParted 0.6.2

Libparted 2.3

Format /dev/sda2 as ext3  00:00:01    ( ERROR )
    	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
    	
path: /dev/sda2
start: 112250880
end: 114352127
size: 2101248 (1.00 GiB)
set partition type on /dev/sda2  00:00:01    ( SUCCESS )
    	
new partition type: ext3
create new ext3 file system  00:00:00    ( ERROR )
    	
mkfs.ext3 -L "" /dev/sda2
    	
mke2fs 1.41.12 (17-May-2010)
/dev/sda2 is apparently in use by the system; will not make a filesystem here!

```

---

### Post by Snoman314 on 2011-03-08
I figured it out. I had incorrectly set up the array and then deactivated it properly, tying up sda2.
The command at the top of the OP works great :)

---

