---
title: "Fstab &amp; Mtab don't match"
date: 2010-07-06
forum: General Help
---

### Post by DapperMe17 on 2010-07-06
Hello,

My HD contains a Windows, Fat32, two Linux & swap partitions. Recently, I had to recover my partition table with "testdisk", due to a foolish attempt to resize a partition.

I recovered all partitions, with the exception of my root partition. I left that unallocated, then reformatted it with GParted, to be of a larger size.

All data has been recovered & the PC works fine, just as it always has.

The wierd thing is that the original "root" partition seems to co-exist on the same partition as my Fat32 data(???)

GParted shows my root partition as almost full, when it should only be about half full....then my Fat32 partition shows empty, when it should be about 3GB full. Root should only be about 5GB, not almost 9GB.

I believe that my mtab & fstab are corrupt relative to the partitions that GParted lists, and need to be fixed. However, I don't know where to start....?


[COLOR="Red"][HTML]fdisk -l[/HTML][/COLOR]


Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae32ae32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1642    13189333+   7  HPFS/NTFS
/dev/sda2            1643        3327    13534762+   f  W95 Ext'd (LBA) 
/dev/sda3            3328        4701    11036655    c  W95 FAT32 (LBA)
/dev/sda4            4702        4864     1309297+  82  Linux swap / Solaris
/dev/sda5            2844        3327     3887698+  83  Linux
/dev/sda6            1643        2843     9646969+  83  Linux


***[COLOR="Blue"]NOTE.../dev/sda2 is an extended partition, which should hold only two EXT4 partitions-sda5 & sda6 [/COLOR]***
_____________________________________________________________________________________
[COLOR="Red"][HTML]/etc/mtab[/HTML][/COLOR]

/dev/sda6 / ext4 rw 0 0
none /proc proc rw 0 0
none /dev/pts devpts rw 0 0
/dev/sda5 /home ext4 rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda3 /media/LINUX\040-\040XP vfat rw,nosuid,nodev,noatime,uhelper=hal,shortname=lower,uid=500,flush,utf8 0 0

_________________________________________________________________________________
[COLOR="Red"][HTML]/etc/fstab[/HTML][/COLOR]

# Entry for /dev/sda6 :
UUID=00d48746-feba-4db5-80a4-a7416ca9b38a / ext4 defaults 1 1
# Entry for /dev/sda5 :
UUID=6cd8b50f-7149-4aa3-94fd-215e7485ec71 /home ext4 defaults 1 2
none /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=a2c83cbf-05b6-4a07-b116-cc7a609f1e44 swap swap defaults 0 0
none /dev/pts devpts defaults 0 0
tmpfs /dev/shm tmpfs defaults 0 0

____________________________________________________________________________________
**[COLOR="Red"]Gparted...see image attachment below.[/COLOR]**


_____________________________________________________________________________________
[COLOR="Blue"]***NOTE...Fat32 shows empty. However, all data that's suppose to be in that partition, is still available, and located somewhere. I wonder if it's being held in the root partition by mistake? Out of curiosity, I tried to save a 700mb file to my Fat32 partition (which shows empty & should have plenty of free space), but it was cancelled due to lack of space on the partition.***[/COLOR]


______________________________________________________________________________________
***[COLOR="Red"]Here's my "testdisk" information (Fat 32 shows a warning...maybe I have to repair the cylinders or heads?)[/COLOR]***

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 40 GB / 37 GiB - CHS 4864 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  1641 254 63   26378667
 2 E extended LBA          1642   0  1  3326 254 63   27069525
Warning: Incorrect number of heads/cylinder 16 (FAT) != 255 (HD)
 3 P FAT32 LBA             3327   0  1  4700 254 63   22073310 [LINUX - XP]
 4 P Linux Swap            4701   0  1  4863 254 63    2618595
 5 L Linux                 2843   1  1  3326 254 63    7775397
   X extended              1642   0  2  2842 254 63   19294064
 6 L Linux                 1642   2  1  2842 254 63   19293939



Thanks for any help!

---

### Post by gzarkadas on 2010-07-07
First, what I see in your listings:

[U]1. `fdisk -l' :
[/U]The start-end blocks of each partition are continuous, with no overlap. Shows OK.

[U]2. `/etc/mtab' :
[/U]Partitions (sda) 1, 3, 5, 6 show mounted, as they should. Looks OK.

[U]3. `/etc/fstab' :
[/U]Only partitions (sda) 5, 6 show. Thus the others are mounted later. How, is the question (maybe the error is there). 
There is an `# Entry for /dev/sda3 :' under the swap UUID. _Maybe you incorrectly mount the fat32 partition as swap_, or it is a left-over comment if you have adjusted the UUID to point to sda4. Check from the System Monitor whether you have swap enabled or not.

[U]4. Gparted image :
[/U]There is an error icon in /dev/sda3. What shows up if you right-click the partition and select `Information' from the popup menu?

[U]5. Testdisk output :
[/U]The start-end blocks of each partition are in sync with fdisk -l (it appears testdisk uses 0-based counting while fdisk 1-based, thus this constant by 1 difference). 
There  is this warning about incorrect number of heads/cylinder, but the numbers shown in the listing make sense and are in (at first view) agreement with the overall sizes of the partitions.

Then, a few trial-and-error suggestions, since I can't give a definite answer about your situation:

-- First check that you do not incorrectly mount your fat32 partition as swap. 

-- Then look up the manuals whether this testdisk warning actually is an error indication or not (sorry, I haven't used testdisk yet). 

-- Then check whether your restore process has left a large number of backed-up files in some location(s) or inside your trash. 
You can use `baobab' to view the size of each part of your tree, or the `du' command. Verify that your disk usage as seen from within the filesystem (by `du' or `baobab') is in sync with the used sizes reported by Gparted. If yes, you have backups / trash left behind. 

If none of the above helps to correct the issue, then we 'll have to review it again.

---

### Post by DapperMe17 on 2010-07-08
Gzarkadas, thank you very much for your time & effort!


To answer a few of your questions...

No, I did not manually mount /sda3 as swap...

Attached is a revised screengrab of my GParted...

Also attached, is a screengrab of the warning information provided for /sda3...

---

### Post by gzarkadas on 2010-07-09
Try to install the packages mentioned at the /dev/sda3 error message (dosfstools, mtools). The output of df -Th you supplied in [that thread]("http://forums.linuxmint.com/viewtopic.php?f=49&t=51196&p=294547") is in sync with the results shown by Gparted. So, it is plausible that the only reason that the fat32 partition shows empty is the lack of the tools needed to access it. 

To find where your filesystems have grown unexpectedly use the du command or a gui tool such as baobab (see my previous post). The best bet is your trash or some backups (maybe partition image files?).

If nothing of these works, it may be the case that the partition table did not succesfullly restored in its entirety. The best thing to do then is backup your partitions and rebuild the hdd from the beginning.

---

### Post by dino99 on 2010-07-09
> **DapperMe17 said:**
> Gzarkadas, thank you very much for your time & effort!


To answer a few of your questions...

No, I did not manually mount /sda3 as swap...

Attached is a revised screengrab of my GParted...

Also attached, is a screengrab of the warning information provided for /sda3...

why fat32 nowadays ?

---

### Post by DapperMe17 on 2010-07-29
Ok...issue with /sda6 is corrected via a reinstall & reformat of that partition.

However, /sda6, which is my shared vfat partition, continues to show empty in Gparted. All of my files are still present and accessible in that folder (Linux - XP). So, they're abviously there, just not showing in Gparted.

Do I need to change my fstab?

---

### Post by gzarkadas on 2010-07-31
Please report whether you have installed the dosfstools and mtools packages as suggested.  Also whether the vfat partition's files being "accesible", as you state, means that you can read/write to that partition. If you can read/write normally and only Gparted does not see the partition contents, then it is a minor, application-specific issue; no need to change the fstab.

---

### Post by DapperMe17 on 2010-08-01
Yes, those two tools are installed. However, still received the error message in Gparted to try installing them...as well as Gparted not showing any data in that shared partition....?

Also, yes the vfat is accessible. I can normally read & write to that partition.

---

### Post by gzarkadas on 2010-08-01
Then it is a gparted-specific error. The only thing I would test before either abandon the issue or filing a report to the gparted project is whether the spaces in the mount path create this behavior. You could create a directory without spaces inside /media (say ostrans) and change the line in your fstab as follows: 

```
/dev/sda3 /media/**ostrans** vfat rw,nosuid,nodev,noatime,uhelper=hal,shortname=lower,uid=500,flush,utf8 0 0
```

Then do a `umount /media/LINUX\ -\ XP' and afterwards a `mount -a'  to remount /dev/sda3 in /media/ostrans. Then fire-up Gparted to see if it now reads the vfat partition contents.

---

### Post by DapperMe17 on 2010-08-01
Thanks,

Will give it a try!

---

