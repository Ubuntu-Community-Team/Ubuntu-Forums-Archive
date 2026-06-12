---
title: "new HDD, mounts but cannot access"
date: 2010-07-30
forum: General Help
---

### Post by capo1949 on 2010-07-30
Hi All
I have an extra HDD to upgrade from 250Mb to 500Mb.

I followed InstallingANewHardDrive in this forum under Community Documentation. 

The drive is mounted automatically and I have given myself ownership.
The problem I have is that I cannot see the additional space in my home directory.
graham@graham-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            231381656 211113260   8514844  97% /
none                   1543356       352   1543004   1% /dev
none                   1547576       364   1547212   1% /dev/shm
none                   1547576       220   1547356   1% /var/run
none                   1547576         0   1547576   0% /var/lock
none                   1547576         0   1547576   0% /lib/init/rw
/dev/sdb1            240362656    191768 237728928   1% /media/newHDD

Do I have to mount the new HDD at the root, I assume that is what the / under "mounted on " indicates?

graham@graham-desktop:~$ cd /media
graham@graham-desktop:/media$ ls -l
total 16
lrwxrwxrwx 1 root   root      6 2009-10-30 16:23 cdrom -> cdrom0
drwxr-xr-x 2 root   root   4096 2009-10-30 16:23 cdrom0
drwxr-xr-x 2 root   root   4096 2009-10-30 16:23 cdrom1
lrwxrwxrwx 1 root   root      7 2009-10-30 16:23 floppy -> floppy0
drwxr-xr-x 2 root   root   4096 2009-10-30 16:23 floppy0
drwxr-xr-x 3 graham graham 4096 2010-07-30 16:42 newHDD

I am being cautious as I dont really understand the process.

Some help would be appreciated

---

### Post by gordintoronto on 2010-07-30
The new hard drive is not your home folder, so its space does not appear there.

Did you partition and format the new drive?

Using Nautilus, you should be able to create folders on the new drive, and move files into those folders.

I would use the command:
sudo fdisk -l
to see what is up with the new drive.

---

### Post by capo1949 on 2010-07-31
Hi 
Thanks for you response.

Yes the drive has been formatted and I can move data onto the new drive.

[COLOR="SandyBrown"]But what I am trying to achieve is to make the new drive continuos from the existing. As at the moment when trying to copy data to my video folder in my home directory the system advised not enough space[/COLOR]
 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=656dc075-ab2b-4cb8-a306-1fdc56fc3179 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b35cf490-d619-4e08-b61b-6f0344ddfb8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /media/newHDD   ext3    defaults     0        2

graham@graham-desktop:~$ sudo fdisk -l

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0b3c0700

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29265   235071081   83  Linux
/dev/sda2           29266       30394     9068692+   5  Extended
/dev/sda5           29266       30394     9068661   82  Linux swap / Solaris

---

### Post by oldfred on 2010-07-31
There are ways to make two drives look like one, but I prefer to just have separate /data and/or /home partitions.

You can move your /home from the / (root) into a newhome and rename/remount as /home.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You can also make data partition that has all your data from /home so home only has your user settings. I do this as I multiboot. It also makes it easier to do a clean install. I litterally have 3 versions of Ubuntu 9.10, 10.04 & 10.10 all using the same data.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
[http://ubuntuforums.org/showthread.php?t=1411482](http://ubuntuforums.org/showthread.php?t=1411482)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by capo1949 on 2010-08-02
Hi Oldfred

Thanks for the post you have given me a lot to think about.

---

### Post by oldfred on 2010-08-02
A little more to think about. 

With partitioning of a new drive it pays to think about what you plan on doing for the next year or two or until you may get a new drive again. Will you be storing lots of data. Possibly thinking about installing another operating system to see if it is better or not? If not 100% sure you can leave some space unallocated as long as you can add it to the extended partition and then add partitions or expand your last partition.

In my case I bought a new drive when Karmic came out and only had root, swap and a small shared NTFS for windows and after a couple of years was using  windows less & less. I moved home into a new 100GB partition, but then decided I wanted a /data so I moved it to another 100GB. My home is now only 1Gb in the 100GB. I also like keeping my old Ubuntu install, and experimenting with the future/beta version, so I have several 20-25GB system partitions that I mount all my data into so they all are similiar data wise. I may or may not copy some settings from /home but do not attempt to share /home.

---

