---
title: "drive in use, mtab says unmounted..."
date: 2011-06-05
forum: General Help
---

### Post by prayersfor.rain on 2011-06-05
Hello!
I'm using live cd 10.10 right now...I made some changes (that were probably really dumb) to grub2 and now when I choose ubuntu it won't start.  The bootloader itself works I believe, as it gives me all the options and I can get into my winxp just fine.  I think I just changed some settings and messed it up.
So I figured I'd either format and fresh install Maverick or repair grub2.  Trying to format the drive (figured that was easiest) I get a message that says the drive is in use.  I don't know what's using it or how to stop it. 
Trying to repair grub2, you have to mount that drive, right? So I try mounting and it again says that the drive is in use. 

First off, here's the results of sudo fsck -l:

```
Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x383dd7ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7298    58621153+   7  HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ee2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      230555  1851931616+   c  W95 FAT32 (LBA)
/dev/sdb2          230555      243202   101582848    5  Extended
/dev/sdb5          230555      242029    92160000   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001595d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       59655   479170560   83  Linux
/dev/sdc2           59655       60802     9212929    5  Extended
/dev/sdc5           59655       60802     9212928   82  Linux swap / Solaris

```The linux on sbd is Zenwalk that I installed without lilo. I think the main reason I'm having trouble booting is because of the changes I made to grub2 to try and get Zenwalk to show up on there (which didn't happen anyway).
 
When I use gparted to try to format sdc, I get 
```

Format /dev/sdc1 as ext4  00:00:02    ( ERROR )
         
calibrate /dev/sdc1  00:00:00    ( SUCCESS )
         
path: /dev/sdc1
start: 2048
end: 958343167
size: 958341120 (456.97 GiB)
set partition type on /dev/sdc1  00:00:02    ( SUCCESS )
         
new partition type: ext4
create new ext4 file system  00:00:00    ( ERROR )
         
mkfs.ext4 -j -O extent -L "" /dev/sdc1
         
mke2fs 1.41.12 (17-May-2010)
/dev/sdc1 is apparently in use by the system; will not make a filesystem here!

```

sdc drive is the one I'm trying to unmount.

When I do sudo umount /dev/sdc (and sdc 1, 2, 5, all done separately), I get:
```

umount: /dev/sdc: not mounted

```When I sudo fsck /dev/sdc
```

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Device or resource busy while trying to open /dev/sdc
Filesystem mounted or opened exclusively by another program?

```Going to /proc/mounts I get
```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=1541960k,nr_inodes=211954,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
aufs / aufs rw,noatime,si=5f87ce70 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
```I don't see /dev/sdc(1,2,5) in there anywhere? Am I missing it?  Maybe I'm not looking for the right thing.  (I'm not too familiar with this stuff, I'm just learning.)
and
/etc/fstab gives me
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdc5 swap swap defaults 0 0
```which is finally something that says something /dev/sdc.
But I don't now what fstab is supposed to tell me in the first place or how to even read what it's saying.


And I apologize that this is just a mishmash of what may be random information.  I tried stuff I got off of a bunch of different people with similar problems (googled all sorts of stuff) and the stuff I posted were the ones I remember seeing the most.  I know there are some things I've forgotten to try again.  

If anyone could help me find out what's running on /dev/sdc and how to turn it off/unmount so I can either try to repair grub2 or do a clean install, that would be awesome.  


Also, when I ran Linux Reader on my WinXP I was able to save all the files I wanted to keep to another drive, but when I try to access that same drive on livecd nothing happens...

Thank you in advance for your help!

---

### Post by WorMzy on 2011-06-05
You can't unmount or fsck an entire disk (except in rare cases where the partition is treated as the entire disk)

Try running

```
sudo swapoff
```

Then you should be able to repartition as you see fit. You don't need to format your Ubuntu partition though, you just need to fix grub2. Unfortunately, I can't help you with that, as I use grub legacy. If you mount your Ubuntu partition and copy-paste your /media/<ubuntu partition>/boot/grub/grub.cfg here, someone may be able to help you fix it.

---

