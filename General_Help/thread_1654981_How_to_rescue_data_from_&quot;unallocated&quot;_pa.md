---
title: "How to rescue data from &quot;unallocated&quot; partition"
date: 2010-12-29
forum: General Help
---

### Post by akira27 on 2010-12-29
While installing Ubuntu 10.04 and 10.10 side by side and re-partitioning my hard drive, I've *somehow* managed to damage the file system.  My first partition was a 100 Gigabytes, and now it's split in two: 43 G Unknown and 56 G Free.  I am unable to access any files in these partitions.

Because the hard drive wouldn't boot, I had to reinstall a Grub2 boot menu.

Interestingly, Disk Utility shows the hard drive as split into 9 partitions, but under gparted the whole drive is shown as unallocated space.  I've tried testdisk and photorec, but was unable to recover any files from what used to be my first partition.

The rest of the hard drive seems to be okay; however, I cannot install a new version of Ubuntu on any partition due to the whole drive being "unallocated".

If someone could offer any suggestions as to how I can recover my files on the first partition, it would be greatly appreciated.

Thank you.

---

### Post by coffeecat on 2010-12-29
> **akira27 said:**
> under gparted the whole drive is shown as unallocated space.

This can happen when there is a problem or impossibility in the partition table data, not in the actual partitions themselves. These problems can be "overlapping" partitions or an extended partition extending beyond the end of the physical drive. If you are lucky, this will be fixable by editing the partition table itself, which is not such a daunting task as it might seem to be.

First, please post the output of the terminal command:

```
sudo fdisk -lu
```Be sure to use the option '-lu' and not '-l' as often recommended in the forum. Please also enclose the output in [noparse]```

```[/noparse] tags to retain essential formatting.

---

### Post by seawolf167 on 2010-12-29
If the problem is just lost partitions, you can use [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")to restore them.

An old how-to from the forums is [here]("http://ubuntuforums.org/showthread.php?t=387922").

---

### Post by akira27 on 2010-12-29
Hi coffeecat and seawolf,

Thank you both for the replies.  Here is the output from sudo fdisk -lu.

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c4817

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2       193581056   218719727    12569336   83  Linux
/dev/sda3       218720256   219914223      596984   82  Linux swap / Solaris
/dev/sda4       219929850   312512444    46291297+   f  W95 Ext'd (LBA)
/dev/sda5       248477696   304013311    27767808   83  Linux
/dev/sda6       304015360   306487279     1235960   82  Linux swap / Solaris
/dev/sda7       306499584   312498159     2999288   82  Linux swap / Solaris
```"sda1" used to be 100 GB, but now when I look at the same drive with Disk Utility, it shows sda1 43GB + sda 56GB (free), then sda2, sda3, then sda again 15GB (free), sda 5, 6, 7 then sda again with "184446744 TB (-6,371,840 bytes)"!!

So definitely the partition table is corrupt.  I am able to use sda5 to boot up, sda2 for little storage.

Seawolf, when I used testdisk, it seemed to recognize all the partitions as the list above, but when it came to rescuing files from sda1, it told me the file system must be damaged. I tried rewriting the boot record, partition table, basically everything testdisk can do, but no luck.

Once again, thank you for the suggestions. I really believe that the data is still there, just the partitions are set incorrectly.

---

### Post by coffeecat on 2010-12-30
Here is the  problem that is causing Gparted to show the drive as unallocated:

> **akira27 said:**
> ```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total [COLOR=Red]312500000[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c4817

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2       193581056   218719727    12569336   83  Linux
/dev/sda3       218720256   219914223      596984   82  Linux swap / Solaris
/dev/sda4       219929850   [COLOR=Red]312512444 [/COLOR]   46291297+   f  W95 Ext'd (LBA)
/dev/sda5       248477696   304013311    27767808   83  Linux
/dev/sda6       304015360   306487279     1235960   82  Linux swap / Solaris
/dev/sda7       306499584   312498159     2999288   82  Linux swap / Solaris
```

See where I've highlighted in red. The end of the extended partition sda4 is showing as being beyond the physical end of the hard drive. The extended partition sda4 is a "container" for your logical partitions, sda5, sda6 and sda7. The boundaries of the logical partitions seem to be OK, except there is an unallocated gap of about 14.6GB in front of sda5.

 Whether that is also the cause of your being unable to retrieve files  from sda1 is unclear. There may be a separate problem with sda1, but you  need to repair the partition table entry for sda4 before doing anything else. Here is a link, written by forum member srs5694, which will tell you how:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Post back if you need help with that. Take your time with it. You just need to double-check everything you do. Once you've done that, Gparted will show your partition layout properly and you can then test sda1. If you still cannot access files from sda1 we can then investigate whether there is filesystem corruption and try to fix it. But don't try to do anything with sda1 until you have repaired the partition table. 

What is on sda1:  Windows  and, if so, which version, or is it just a data partition?

---

### Post by akira27 on 2010-12-30
Great, very helpful advice! I will try to fix the partition entry table for sda4, according to the link you sent.

As for sda1, it had an Ubuntu kernel (old one) and was used as data space.  One problem with it now is that of the total 100Gb which was mostly full, 56Gb of it is currently shown as "free". But there are files in there.

Well, first I will solve sda4 and post the result.

---

### Post by akira27 on 2010-12-30
Ok, so I backed up my old partition table using this command:

```
sfdisk -d /dev/sda > oldparts.txt
```Then I edited it to correct the size of the extended partition (sda4), by subtracting the start number from the total number of sectors.  I wrote the new partition table to the disk:

```
sfdisk /dev/sda < newparts.txt
```Here was the result (edited):

```
Disk /dev/sda: 19452 cylinders, 255 heads, 63 sectors/track
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  83891429   83891367   7  HPFS/NTFS
/dev/sda2     193581056 218719727   25138672  83  Linux
/dev/sda3     218720256 219914223    1193968  82  Linux swap / Solaris
/dev/sda4     219929850 312499999   92570150   f  W95 Ext'd (LBA)
/dev/sda5     248477696 304013311   55535616  83  Linux
/dev/sda6     304015360 306487279    2471920  82  Linux swap / Solaris
/dev/sda7     306499584 312498159    5998576  82  Linux swap / Solaris
Warning: partition 2 does not start at a cylinder boundary
Successfully wrote the new partition table
```The warning about partition 2 worries me, because it's the only partition that can boot at this point.  I will try running gparted to see what it shows.

---

### Post by coffeecat on 2010-12-30
> **akira27 said:**
> As for sda1, it had an Ubuntu kernel (old one) and was used as data space.  One problem with it now is that of the total 100Gb which was mostly full, 56Gb of it is currently shown as "free". But there are files in there.

Your fdisk output shows the size of sda1 as 43GB with 56GB free space coming next. One of two things may have happened. The partition may simply have been shrunk and all the data is in the 43GB. But more likely, if something went wrong, is that the end boundary in the partition table was rewritten but the data is, as you say, now sitting in the free space. We'll look into that once you've got Gparted showing partitions, but don't use Gaprted to try to manipulate sda1. One other thing; you say it had an Ubuntu kernel which suggests it was a Linux partition. But it's showing as NTFS, a Microsoft filesystem. Can you clarify?

> **akira27 said:**
> The warning about partition 2 worries me,

It's a common warning. It's often of little practical consequence.

---

### Post by akira27 on 2010-12-30
It's looking promising.  Gparted now shows the whole hard drive in partitions, instead of one big unallocated space.

However, when I click on sda1, it shows this error message:

```
$MFT has invalid magic.
mtfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
Failed to mount '/dev/sda1': Input/output error.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
```That is odd that it tells me to use a Windows program.  Would testdisk be able to fix this inconsistent NTFS?
Also I'm not sure if the sda1 partition should be NTFS.

Here are the partitions as it appears in gparted:
```

40Gb     sda1 (ntfs)
52Gb     unallocated (should contain files)
12Gb     sda2 (ext4)
.5Gb      sda3
7Mb       unallocated
44Gb     sda4 (extended)
     13Gb     unallocated
     26Gb     sda5 (ext4)
     1Mb      unallocated
     1Gb      sda6 (linux-swap)
     6Mb      unallocated
     2Gb      sda7 (linux-swap)
```I must clean it all up to just 2 or 3 partitions, after I rescue my data from sda1. I don't know what's with all the unallocated space, they must have been created when I did the damage in the first place.

---

### Post by coffeecat on 2010-12-30
Have a look at my post #8 - I think you missed it.

NTFS is a Microsoft filesystem and can only be repaired with MS tools, i.e. chkdsk. However, I am not convinced it was a NTFS partition to start with. Perhaps when the partition table damage was done, the filesystem type was changed in the partition table. This is only one or two bytes.

I'll await your response to my question in post #8 before going further.

---

### Post by akira27 on 2010-12-30
Hi coffeecat,

I just saw your reply. Thank you for helping me in this process.

When I first got the computer, it was a Windows system, and I installed Ubuntu
over it -- perhaps it kept the NTFS on sda1? But that's unlikely, I'm quite sure
I formatted the whole drive when installing Ubuntu.  I believe sda1 shouldn't be
NTFS but somehow got changed.

I will now try testdisk to see if it recognizes sda1 and the files in it.  Isn't it possible
in testdisk to change NTFS to another type?

In addition, what I would like to do is merge sda1 with the 50Gb unallocated space after it,
as they should be one 100Gb partition.

---

### Post by coffeecat on 2010-12-30
> **akira27 said:**
> I will now try testdisk to see if it recognizes sda1 and the files in it.

Good luck, but in case it does not help, let me give you a possible scenario of what might have happened. I'll assume that the partition was always formatted NTFS.

When the damage occurred, the end boundary of the partition was rewritten in the partition table which resulted in the partition showing as only 43GB. But the filesystem still occupies all of the 100GB. The MFT (master file table), an essential part of the NTFS filesystem, often sits up the end of the partition - hence the error about $MFT.

If this is so - and this is only a theory - then you could try shifting the end partition boundary up to just before sda2, using the technique you have already used for fixing sda4. Then, *perhaps* the filesystem will become valid again and you would be able to retrieve your files.

Alternatively, there is photorec for file recovery which comes as part of testdisk. This is a last resort though. You get thousands of files with arbitrary filenames which you have to sort through manually - a wretched task.

---

### Post by akira27 on 2010-12-30
As per your suggestion, I corrected the size of sda1 to be just before sda2:
 
 ```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   193581055    96790496+   7  HPFS/NTFS
/dev/sda2       193581056   218719727    12569336   83  Linux
/dev/sda3       218720256   219914223      596984   82  Linux swap / Solaris
/dev/sda4       219929850   312499999    46285075    f  W95 Ext'd (LBA)
/dev/sda5       248477696   304013311    27767808   83  Linux
/dev/sda6       304015360   306487279     1235960   82  Linux swap / Solaris
/dev/sda7       306499584   312498159     2999288   82  Linux swap / Solaris

```Now gparted shows sda1 as 92Gb NTFS, but still displayed the same error message about invalid magic and $MFT.

Should I try changing sda1 from NTFS to a Linux type using testdisk?

---

### Post by coffeecat on 2010-12-30
> **akira27 said:**
> Should I try changing sda1 from NTFS to a Linux type using testdisk?

To be honest, I don't know. If it was my machine that is what I would probably try. The problem is, do you choose ext3 or ext4? Unless you know what it was originally, it's going to be a guess. A few posts back you mentioned an Ubuntu kernel. Can you remember which version of Ubuntu this belonged to? Was sda1 used as a Linux root or boot partition at one point?

I'll try to summon up a couple of second opinions for you. Hang in there! :)

---

### Post by akira27 on 2010-12-30
I changed sda1 from NTFS to Linux type (number 83 in Testdisk), but when I tried to list the files, the software aborted with "segmentation fault". I believe sda1 used to have a kernel, but cannot remember which version, and it doesn't show up on the Grub2 menu. It used to be a Linux boot partition some time ago. I suppose the last option is, as you suggested, to use Photorec to recover what I can. I'm not looking forward to it, but at least I can (hopefully) salvage what is essential.

---

### Post by akira27 on 2010-12-30
Here's an update on the situation. I'm still unable to see any files on my poor sda1, but I haven't given up yet.  This page has given me hope: [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/"), an open-source data recovery software toolkit.

Now that the partition table is fixed -- thanks to coffeecat! -- I will try to extract files using the following software: Foremost, Magic Rescue and Photorec.

---

### Post by coffeecat on 2010-12-31
I've had a little discussion by pm with a couple of forum friends. When you've finished with Rescue Remix (good find!) and the others and recovered whatever files you can, here's a suggestion:

Run photorec again and change sda1 back to ntfs. All you're doing by that is changing the filesystem code number in the partition table. The reason for this is that I have a feeling in my bones that the partition should be NTFS from what you've posted. Then go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file (in code tags). In your situation there will be a lot of irrelevant detail in that, but I would like to see what is in the boot sector of sda1. Since sda1 used to be a Windows partition and if it was never reformatted from NTFS, then there might still be some Windows boot files in there. That will confirm that the partition should be NTFS and it would be then worth running chkdsk on it. You don't have Windows on that machine, I know, but there are ways of getting chkdsk - we can come to that if necessary.

---

### Post by akira27 on 2011-01-02
I've realized that I would need a new hard drive to recover whatever files are left on my first partition.
Photorec estimated 2 hours of spitting out files with arbitrary names, ugh.

The good news is that after the partition table was fixed, I was able to install Ubuntu 10.10 on sda8,
and migrate my settings from another partition, sda5.

I gave the boot_info script a try, and it gave me the following information.  It's true what you said, coffecat,
sda1 is shown as a Windows format. Perhaps you suggest using chkdsk (?) with wine?

```
Boot Info Summary: =======

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: _________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

======== Drive/Partition Info: ==========

Drive: sda ___________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   193,581,055   193,580,993   7 HPFS/NTFS
/dev/sda2         193,581,056   218,719,727    25,138,672  83 Linux
/dev/sda3         218,720,256   219,914,223     1,193,968  82 Linux swap / Solaris
/dev/sda4         219,914,238   312,498,159    92,583,922   f W95 Ext d (LBA)
/dev/sda5         248,477,696   304,013,311    55,535,616  83 Linux
/dev/sda6         304,015,360   306,487,279     2,471,920  82 Linux swap / Solaris
/dev/sda7         306,499,584   312,498,159     5,998,576  82 Linux swap / Solaris
/dev/sda8         219,914,240   248,477,695    28,563,456  83 Linux


blkid -c /dev/null: _________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        17792ebb-0f72-40f1-a897-7c2b02aa1446   ext4                                     
/dev/sda3        a6936db7-8ab2-4be7-bbb6-ae055d63eb78   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ae936810-0874-4468-823b-4d7204f0c1e3   ext4       akira                         
/dev/sda6        e08885e0-09c6-4dd7-8952-f9ed158d88dc   swap                                     
/dev/sda7        b3e91d38-557b-4f2a-8487-c1c510f29871   swap                                     
/dev/sda8        5d1fca8b-664f-47cc-8027-dd47c64e6dba   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============= "mount | grep ^/dev  output: ==============

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/akira             ext4       (rw,nosuid,nodev,uhelper=udisks)
```

---

### Post by coffeecat on 2011-01-02
I don't think you can run chkdsk from wine, although if you have wine it might be worth seeing if it's included. You need either an installed Windows or a bootable CD/DVD with chkdsk. If you have access to a Windows machine and you have a USB enclosure that would take your hard drive, the easiest way would be to put the drive in the enclosure, plug it into the Windows machine and run chkdsk that way.

If not, do you have access to a Windows installation CD/DVD (XP, Vista or W7) or a Vista/Windows 7 repair disk? You can run chkdsk from the command prompt from those. It has to be a Microsoft disk, not an OEM restore image. If you haven't, you can download either a Vista or W7 repair disc here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Alternatively - and I have no experience of this - I've read that Hiren's boot CD includes a mini-XP with chkdsk. Hiren's Boot CD:

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Download page:

[http://www.hirensbootcd.org/download.html](http://www.hirensbootcd.org/download.html)

---

### Post by akira27 on 2011-01-03
Great! I will try Hiren's boot CD, it seems to have all the rescue software I need for extracting files out of the corrupt partition with NTFS file system.

---

