---
title: "External won't automount"
date: 2010-06-02
forum: General Help
---

### Post by Comrade42 on 2010-06-02
Hello,
After some weeks of use and occasional unplugging-when-busy, my 500GB external USB hard drive no longer will automatically mount when I plug it in. 

The blue light lights up when I plug it in, but there is no automounting behavior. Also, when I type

```
tom@zeppelin:~$ sudo mount -a
```

nothing happens. The result of fdisk:

```
tom@zeppelin:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12154    97622070+   7  HPFS/NTFS
/dev/sda2           18703       19458     6062080   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3           12155       18338    49672980   83  Linux
/dev/sda4           18339       18702     2923830   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7cb6806

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)

```

The only way I can mount the drive is by the following command:

```
tom@zeppelin:~$ sudo mount /dev/sdb1 /media/d -t vfat

```

which I feel is quite explicit and somewhat troublesome, especially since the drive used to automount just fine.

When I call "ls" in the manually mounted drive I find all the files I was expecting, plus some strange new files with question marks and percents in their names:

```
tom@zeppelin:~$ cd /media/d/
tom@zeppelin:/media/d$ ls
'?%                          iTunes Music
'?%                          Media
'?%                          $recycle.bin
'?%                          stuff
'?%                          Ubuntu_Fileback
64bit                        Windows 7 Professional (x64) - DVD (English)
cs50                         Windows 7 Professional (x86) - DVD (English)
Diablo2                      Windows_Fileback
Duncan's Life, just in case

```

Sorry if I've overdocumented this or if my problem is easily solved elsewhere - I would just like to know if there is a fix to my current problem.
Thanks very much!

---

### Post by Comrade42 on 2010-06-03
Reading some other posts inspired me to check my "fstab" file.
Here's what's in it, in case that would help shed some light on my situation.
```
tom@zeppelin:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1e74b0c7-55b1-4b93-8a22-95983f7614cd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=2152aaa6-f45b-4663-b85c-140bca539eed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Much thanks to anyone who can help me understand what's going on! (:

---

### Post by Comrade42 on 2010-06-03
Update: when I plug the external drive in while booted into Windows XP, the drive does a good auto-mount (it appears as my F:\ drive and its name is properly displayed) but none of its contents are properly visible, except for two directories that I've created (using sudo mkdir in Ubuntu) since these problems began. I'm worried that if I don't fix something I could do serious damage to the data on this drive, and those weird files with percents in their names don't make sense.


```
F:\>dir
 Volume in drive F is GANTRITHOR
 Volume Serial Number is 1C0D-2772

 Directory of F:\

01/07/2044  12:00 AM     3,758,205,791 'Ç%
03/10/2010  10:39 PM    <DIR>          .Trash-1000
01/07/2044  12:00 AM     3,758,206,303 'Ç%
05/31/2010  07:00 PM    <DIR>          64bit
01/07/2044  12:00 AM     3,758,206,815 'Ç%
06/01/2010  09:29 AM    <DIR>          stuff
01/07/2044  12:00 AM     3,758,207,327 'Ç%
               4 File(s) 15,032,826,236 bytes
               3 Dir(s)  320,611,352,576 bytes free

```
Recall that this is the exact same drive from before.

Does anyone have any idea what might be going on, or any advice for me? I apologize for these consecutive posts but it seems like it's tricky to get anyone's attention.

---

### Post by dcstar on 2010-06-03
> **Comrade42 said:**
> Hello,
After some weeks of use and **occasional unplugging-when-busy**, my 500GB external USB hard drive no longer will automatically mount when I plug it in. 
........

You do know why you are told to unmount drives before removing them, don't you?

```
man fsck
```

---

### Post by meoow on 2010-06-03
I think your hard disk is damaged.
may some data recovery softwares could help to rescue files you lost,but I'm afraid formatting your hard disk is the only way to fix your current issue.

---

### Post by dino99 on 2010-06-03
install mountmanager and set your prefs (system admin mountmanager)

---

### Post by Comrade42 on 2010-06-03
I did this:

```
tom@zeppelin:~$ sudo fsck /dev/sdb1 -t vfat -y
fsck from util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
FSINFO sector has bad magic number(s):
  Offset 0: 0x00000008 != expected 0x41615252
  Offset 484: 0x00000040 != expected 0x61417272
  Offset 510: 0x0000 != expected 0xaa55
  Auto-correcting it.
/'\200%\000&#2026;\001&#65533;.\000\000\000
  Bad file name.
  Auto-renaming it.
  Renamed to 000\0000000.\000\000\000
/'\200%\000&#2028;\001&#65533;.\000\000\000
  Bad file name.
  Auto-renaming it.
  Renamed to 001\0000000.\000\000\000
/'\200%\000&#2030;\001&#65533;.\000\000\000
  Bad file name.
  Auto-renaming it.
  Renamed to 002\0000000.\000\000\000
/'\200%\000&#2032;\001&#65533;.\000\000\000
  Bad file name.
  Auto-renaming it.
  Renamed to 003\0000000.\000\000\000
/'\200%\000&#2034;\001&#65533;.\000\000\000
  Bad file name.
  Auto-renaming it.
  Renamed to 004\0000000.\000\000\000
/000\0000000.\000\000\000
  Start cluster beyond limit (1073741861 > 15258275). Truncating file.
/000\0000000.\000\000\000
  File size is 3758205791 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/001\0000000.\000\000\000
  Start cluster beyond limit (1073741861 > 15258275). Truncating file.
/001\0000000.\000\000\000
  File size is 3758206303 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/002\0000000.\000\000\000
  Start cluster beyond limit (1073741861 > 15258275). Truncating file.
/002\0000000.\000\000\000
  File size is 3758206815 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/003\0000000.\000\000\000
  Start cluster beyond limit (1073741861 > 15258275). Truncating file.
/003\0000000.\000\000\000
  File size is 3758207327 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/004\0000000.\000\000\000
  Start cluster beyond limit (1073741861 > 15258275). Truncating file.
/004\0000000.\000\000\000
  File size is 3758207839 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
Reclaimed 16449 unused clusters (539000832 bytes) in 151 chains.
Free cluster summary uninitialized (should be 9784282)
  Auto-setting.
Performing changes.
/dev/sdb1: 182861 files, 5473992/15258274 clusters

```

and then a minute later the drive automatically unmounted itself and re-mounted using its proper name (GANTRITHOR) and gave me full read/write access. I think I fixed it! Will report back with further problems if they arise.

Edit: Things are going swell - thanks to all for the advice!

---

