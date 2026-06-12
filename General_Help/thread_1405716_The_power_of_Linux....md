---
title: "The power of Linux..."
date: 2010-02-13
forum: General Help
---

### Post by jblaven on 2010-02-13
Alright, 

I have a HUGE issue.  I have an external HD that now is not being recognized in Vista.  It has two partitions.  One with OSx86 that WAS bootable when connected, the 2nd partition I used for file transfers from different computers (Windows).

Now, I can't get to any of my files.  I tried to go into Vista and give the two partitions drive letters, but to no avail.

As it stands now, I am looking at my ubuntu desktop with an icon of my usb HD.  It's called "193 GB Filesystem"

Is there any way to use Linux to try and fix OR access these files on this HD?

Man, I am ticked #-o

---

### Post by QIII on 2010-02-13
You can't see the contents in either Vista or Ubuntu?

Can you see files on other USB devices?

Can the actual drive be removed from the housing so you can install it as a drive inside your case?


(I've retrieved files a number of times using things like PhotoRec and TestDisk, so there's always that.)

---

### Post by jken146 on 2010-02-13
Does double-clicking on that icon not work?

Could you post the output of ```
sudo fdisk -l
``` please?

---

### Post by lukeiamyourfather on 2010-02-13
The OS X partition is probably not going to be accessible in Linux (since its HFS+ only readable by OS X). The Windows partition will probably be readable in Linux just fine assuming the disk hasn't failed or been damaged. Cheers!

---

### Post by jblaven on 2010-02-13
> **jken146 said:**
> Does double-clicking on that icon not work?

Could you post the output of ```
sudo fdisk -l
``` please?


Here ya go.


joe@joe-desktop:~$ sudo fdisk -l
[sudo] password for joe: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38883825

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48053   385984867    7  HPFS/NTFS
/dev/sda2           48054       51579    28322595   83  Linux
/dev/sda3           51580       60558    72123817+  83  Linux
/dev/sda4           60559       60801     1951897+   5  Extended
/dev/sda5           60559       60801     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0642145

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23488   188664641   83  Linux
/dev/sdb2   *       23488       38914   123905024   82  Linux swap / Solaris
joe@joe-desktop:~$

---

### Post by bruno9779 on 2010-02-13
sda should be your external drive, by how you described it.

sda1 looks like is your macosx partition

I don't see any NTFS so you should try and recover it with testdisk

---

### Post by Roasted on 2010-02-13
> **bruno9779 said:**
> sda should be your external drive, by how you described it.

sda1 looks like is your macosx partition

I don't see any NTFS so you should try and recover it with testdisk

Um, what?

Device Boot Start End Blocks Id System
**/dev/sda1 * 1 48053 385984867 7 HPFS/NTFS**
/dev/sda2 48054 51579 28322595 83 Linux
/dev/sda3 51580 60558 72123817+ 83 Linux
/dev/sda4 60559 60801 1951897+ 5 Extended
/dev/sda5 60559 60801 1951866 82 Linux swap / Solaris

SDA1 looks like your Windows partition...

---

### Post by jken146 on 2010-02-13
First of all, I'll assume that sda *is* your external hard disk.

You should attempt to mount the partitions and recover files from them.
```
sudo mkdir /mnt/foo
sudo mount /dev/sda2 /mnt/foo
cd /mnt/foo
ls

```


When you want to unmount a partition:
```
sudo umount /mnt/foo
```


And if you want to see what is currently mounted where:
```
mount
```

---

### Post by jblaven on 2010-02-13
> **jken146 said:**
> First of all, I'll assume that sda *is* your external hard disk.

You should attempt to mount the partitions and recover files from them.
```
sudo mkdir /mnt/foo
sudo mount /dev/sda2 /mnt/foo
cd /mnt/foo
ls

```
When you want to unmount a partition:
```
sudo umount /mnt/foo
```
And if you want to see what is currently mounted where:
```
mount
```

There should be an OSx partition on the external drive...  can you tell which one it is now?

---

### Post by jken146 on 2010-02-13
> **jblaven said:**
> There should be an OSx partition on the external drive...  can you tell which one it is now?

/dev/sda1

---

### Post by Roasted on 2010-02-14
Can someone fill me in on how sda1 is the OSX partition?

---

### Post by jken146 on 2010-02-14
Actually, I don't know for sure. IIRC OSX uses HFS-plus (which is what the HPFS would be referring to). But you can just mount it and take a look at what files are there.

---

### Post by lukeiamyourfather on 2010-02-14
> **jken146 said:**
> Actually, I don't know for sure. IIRC OSX uses HFS-plus (which is what the HPFS would be referring to). But you can just mount it and take a look at what files are there.

HPFS refers to the link below. It also says HPFS/NTFS, so its probably the Windows partition and NTFS.

[http://en.wikipedia.org/wiki/High_Performance_File_System](http://en.wikipedia.org/wiki/High_Performance_File_System)

Its not related to HFS+ or OS X. Linux will probably not recognize HFS+ at all is my guess since its supported only in OS X. Cheers!

---

### Post by Roasted on 2010-02-15
> **lukeiamyourfather said:**
> HPFS refers to the link below. It also says HPFS/NTFS, so its probably the Windows partition and NTFS.

[http://en.wikipedia.org/wiki/High_Performance_File_System](http://en.wikipedia.org/wiki/High_Performance_File_System)

Its not related to HFS+ or OS X. Linux will probably not recognize HFS+ at all is my guess since its supported only in OS X. Cheers!

Which kind of solidifies my original idea.

SDA1 is indeed your WINDOWS partition.

---

### Post by jken146 on 2010-02-15
Beg your pardon.

---

### Post by lukeiamyourfather on 2010-02-15
> **jken146 said:**
> Beg your pardon.

There's too many acronyms, I had to Wikipedia that one before posting to be sure. Cheers!

---

### Post by jocko on 2010-02-15
> **jblaven said:**
> Here ya go.


joe@joe-desktop:~$ sudo fdisk -l
[sudo] password for joe: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38883825

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48053   385984867    7  HPFS/NTFS
/dev/sda2           48054       51579    28322595   83  Linux
/dev/sda3           51580       60558    72123817+  83  Linux
/dev/sda4           60559       60801     1951897+   5  Extended
/dev/sda5           60559       60801     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072932352 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0642145

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23488   188664641   83  Linux
/dev/sdb2   *       23488       38914   123905024   82  Linux swap / Solaris
joe@joe-desktop:~$
None of those drives look like the external drive you described. Are you sure the external drive was plugged in when you ran "sudo fdisk -l"?
Just to make sure: You have two internal hard drives (one 500Gb, one 320Gb), right?

---

### Post by jblaven on 2010-02-15
> **jocko said:**
> None of those drives look like the external drive you described. Are you sure the external drive was plugged in when you ran "sudo fdisk -l"?
Just to make sure: You have two internal hard drives (one 500Gb, one 320Gb), right?

No, actually the 320GB is a Segate FreeAgent Go.

[IMG]http://www.seagate.com/images/ProductPhoto/Free%20Agent/freeagent_go/fa_go_silver_front_01_320x340.png[/IMG]

---

### Post by jirah on 2010-02-15
Folks, the HPFS in that line is just a hold over from IBM/OS2, nothing Mac related. 
After re-reading the first post, I need to ask if you ever actually tried accessing the drive from the icon you said you were looking at on your desktop. A simple dbl-click would answer the question of whether or not you can access the files and transfer them to another disk. I did see someone else ask the question in the same post that suggested showing the fdisk -l. You answered the fdisk -l, but never the first part of the question, have you actually tried accessing the disk from that icon?

---

### Post by jocko on 2010-02-15
> **jblaven said:**
> No, actually the 320GB is a Segate FreeAgent Go.

Ok, so you have two external drives... That's not the point, your fdisk output did not show the drive you are having trouble accessing (the "193Gb" drive with your osx86 and windows (fat? ntfs?) partitions)...
Was it actually connected when you ran "fdisk -l"?
If not, connect it an run it again.
If it *was* connected the problem may be that the drive itself or it's ata (or sata) to usb adapter is broken.

---

### Post by tomdkat on 2010-02-15
I'm running Ubuntu 9.10 64-bit and I've got an IDE HDD from a PowerMac running Mac OS 9.2 connected to my system using an external USB HDD enclosure.

As soon as I plugged in the HDD enclosure (after putting the HDD from the PowerMac in it), Nautilus mounted the drive and displayed a folder with the contents.

```

tom@deathstar:~$ sudo fdisk -l

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29cc29cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3916    31455238+  83  Linux
/dev/sdb2            3917        4438     4192965   82  Linux swap / Solaris
/dev/sdb3            4439       10966    52436160    5  Extended
/dev/sdb4           10967       19457    68203957+  83  Linux
/dev/sdb5            4439       10966    52436128+  83  Linux

**Disk /dev/sdg: 40.0 GB, 40020664320 bytes**
64 heads, 32 sectors/track, 38166 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

**Disk /dev/sdg doesn't contain a valid partition table**
tom@deathstar:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw)
/dev/sda1 on /mnt/vbox type ext4 (rw,nosuid,nodev,relatime)
/dev/sdb4 on /mnt/data type ext3 (rw,nosuid,nodev,relatime)
/dev/sdb5 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
**/dev/sdg9 on /media/G4 1 type hfsplus (rw,nosuid,nodev,uhelper=devkit)**
tom@deathstar:~$ dir -l "/media/G4 1"
total 578912
drwxr-xr-x 1 root root        18 2007-06-23 15:26 Applications\ (Mac\ OS\ 9)
drwxr-xr-x 1 root root         2 2007-06-28 13:25 Cleanup\ At\ Startup
-rw-r--r-- 1 root root    614400 2008-06-29 00:56 Desktop\ DB
-rw-r--r-- 1 root root   1782658 2007-07-02 09:38 Desktop\ DF
drwxr-xr-x 1 root root        32 2007-09-05 10:42 Desktop\ Folder
drwxr-xr-x 1 root root         5 2006-09-24 12:13 Documents
-rw-r--r-- 1 root root     46080 2006-05-17 16:02 Email\ report
drwxr-xr-x 1 root root         6 2005-07-20 11:24 LiveUpdate\ Folder
-rw-r--r-- 1 root root    355486 2008-06-29 01:02 NAV&#8482;\ 7.0\ QuickScan
-rw-r--r-- 1 root root    414208 2007-10-05 17:25 Norton\ FS\ Data
-rw-r--r-- 1 root root       100 2008-06-29 01:02 Norton\ FS\ Index
-rw-r--r-- 1 root root   6280192 2008-06-26 04:49 Norton\ FS\ Volume
-rw-r--r-- 1 root root   6280192 2008-06-29 01:02 Norton\ FS\ Volume\ 2
drwxr-xr-x 1 root root         9 2005-07-20 11:24 Norton\ SystemWorks\ Folder
-rw-r--r-- 1 root root     27449 2006-11-13 11:18 Print\ file
drwxr-xr-x 1 root root         5 1998-12-04 10:46 Stylus\ Color\ 740\ Driver
drwxr-xr-x 1 root root        43 2008-06-29 01:02 System\ Folder
drwxr-xr-x 1 root root         3 2005-04-06 00:00 TheFindByContentFolder
drwxr-xr-x 1 root root         4 2005-08-30 16:01 TheVolumeSettingsFolder
drwxr-xr-x 1 root root       456 2007-09-26 12:38 Trash
drwxr-xr-x 1 root root         7 2005-03-08 12:14 Utilities
-rw-r--r-- 1 root root 547356672 2008-06-29 00:53 VM\ Storage
drwxr-xr-x 1 root root         7 2005-02-19 10:36 Xerox\ Laser\ Printer
tom@deathstar:~$ 

```
Linux can mount and read HFS+ partitions.

Peace...

---

### Post by jblaven on 2010-02-15
Well,

I decided to reformat it since I couldn't get it to work in any OS.  Windows, Linux, OSx86.  At least in Linux, I was able to reformat it and start over.

---

### Post by lukeiamyourfather on 2010-02-15
> **tomdkat said:**
> 
Linux can mount and read HFS+ partitions.

I just saw that in the man page for mount, good to know! It wasn't long ago when I looked into this and found there was no support for HFS+. My Apple user friends will be thankful for your info. Cheers!

---

