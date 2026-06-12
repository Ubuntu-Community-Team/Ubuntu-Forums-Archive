---
title: "Deleted grub in Windows - what can I do?"
date: 2011-09-30
forum: General Help
---

### Post by tomkat3 on 2011-09-30
In short, I've been running Xunbuntu 11.04 alongside Windows 7 in a hard drive partition. Today I accidentally deleted the hard drive partition that contained grub (I think) that allowed me to choose my operating system whenever I booted up. My question is, is there a way to recover the data?

Here's the long version:

Up until this morning, I had been happily running Xubuntu via a hard drive partition alongside Windows 7. I use lots of software that only runs on windows (a problem I'm working on), so ran Xubuntu on a 10GB partition, and left the rest to windows. I wanted to expand Xubuntu's 10GB to 30GB, so I had defragged the windows partition to prepare.

Now, I originally created and named the partition I installed Ubuntu on 'LINUX', but after Xubuntu was installed, I saw that LINUX was reduced to 32MB and the rest of the 10GBs I had allotted was called 'free space' or something similarly anonymous. When using Ubuntu, LINUX was listed as another mounted filesystem.

It seemed separate from my Ubuntu installation, since it was mounted after all, so when I went into windows to expand the partition that contained Ubuntu, I deleted the LINUX partition just to clean things up. A more cautious part of me instantly said, "Waaait..." so I rebooted, and saw 'grub_rescue>'.

I'd like to think I didn't erase all the data in the 10GB partition, since I only told windows to delete the 32MB partition. Is there a way to set up grub again and perhaps get everything back to normal?

---

### Post by MG&amp;TL on 2011-09-30
Three ways I have found:

1. Install grub again: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
2. Use your windows recovery partition, boot to a command-line and run :```
fixmbr
```
Then you can boot to windows and clean up linux partitions.

3. Reinstall xubuntu.

---

### Post by oldfred on 2011-09-30
Windows does not properly see the Linux partitions. The Windows partitioner is really only useful for shrinking the Windows partion. Everything else use gparted or other partitioning tools from Linux.

You could use testdisk to see what it says.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by garvinrick4 on 2011-09-30
Put you live cd in (install Cd and use Try Ubuntu) when boots open a terminal and:
```
sudo fdisk -l
```Lower case L
```
sudo parted -l
```Lower case L
Copy and paste them here. I was just going to check and see if there was still a linux partition and if so how big?

---

### Post by tomkat3 on 2011-09-30
So I'm using the same computer, but I'm running it off of a puppy Linux live usb. I've only been using Linux for about a year, so I'd really appreciate it if someone told me what all this means.

```

sh-4.1# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          18      144553+  de  Dell Utility
/dev/sda2   *          19       13319   106833920    7  HPFS/NTFS
/dev/sda3           13323       14594    10207233    5  Extended
/dev/sda5           14534       14594      482304   82  Linux swap / Solaris

Disk /dev/sdb: 1002 MB, 1002438656 bytes
31 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018      978267    c  W95 FAT32 (LBA)

Disk /dev/sdc: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders
Units = cylinders of 735 * 512 = 376320 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       21270     7816688    b  W95 FAT32

```

```

sh-4.1# parted -l

Model: ATA SAMSUNG HM121HI (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  148MB  148MB   primary   fat16           diag
 2      149MB   110GB  109GB   primary   ntfs            boot
 3      110GB   120GB  10.5GB  extended
 5      120GB   120GB  494MB   logical   linux-swap(v1)


Model: USB Flash Disk (scsi)
Disk /dev/sdb: 1002MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  1002MB  1002MB  primary  fat32        boot, lba


Model: SanDisk Cruzer (scsi)
Disk /dev/sdc: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32


```

---

### Post by garvinrick4 on 2011-09-30
It means you have 
sda1 a dell utility partition 148 meg
sda2 your windows install of 109 gig (windows is NTFS format) (linux is now ext4 format, in which you have none left in your partition table)
sda3 an extended partition of 10.5 gig (extended a house for logical partitions where your linux survived)
sda5 a 500 meg logical partition where your swap is.

Seems as though there is 10 gig left in your extended partition being unused. (I imagine where your linux was before deleting it)

So you have to make extended partition larger to house a bigger logical partition for Linux.
Delete swap can make a larger one than 500 meg. (they say twice the size of installed Ram) according to how much ram installed do not need to get crazy 2 gig plenty.

oldfred gave you some links to data recovery!!

Or you can just download a version of Ubuntu you want and reinstall. Here is the link with "How to do it" and download. Do what you are comfortable with of course.
Read up on partitioning for a bit. 3 types Primary, extended,logical and only allowed 4 primarys and extended counts as 1 but you can have all the logical's you want
with linux residing in the logicals starting at sda5 and up. So the size of the extended is the key. Read a bit, pretty self explanitory. 
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by garvinrick4 on 2011-09-30
If you want to get Windows booting: Only a couple of easy commands with your windows disk.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

I am going to log off and go to dinner oldfred has been around (well he is oldfred that says it) a nice guy and
he will have this thread subscribed so will answer and help if need anymore) There are actually just
a lot of good users willing and able to help in these Forums.

---

### Post by oldfred on 2011-09-30
If the 10GB is unallocated in the extended partition, I would think testdisk might recover it completely.

I do not know if you can run testdisk from Puppy or not. The newer Puppy has access to the Ubuntu repository. Some rescue LInux liveCDs include testdisk as standard.

gparted also has a recover partition capability. Not seen it used.  One user used parted to recover a partition but he had a good idea of start & end sectors as it requires that to work.

Can you download from another PC other liveCDs? I always recommend that you have a liveCD or repair CD for every system installed. And being a belt & suspenders type, I usually have several additional bootable ISO on my flash drive. I used to burn a bunch of CDs but I used to use so many I switched to flash drives.

---

### Post by tomkat3 on 2011-10-01
Ok, sorry for the delayed response.

So I'd really like to use my Windows 7 disk to simply fix that bootloader, but my problem is that my windows 7 disk is 600 miles away at home (I'm a university student) and none of my friends seem to have theirs.

I tried to restore the partition using testdisk, but I fear I may have made things worse. I used testdisk to write the 32MB partition as primary bootable, which may not have been as correct as it sounded. 

I can't exactly copy/paste the results, since I'm using a computer in the library (and my puppy usb can't seem to connect to the wireless), but fdisk and parted only seem to find one partition. I'll type things out as best I can:

```
#fdisk- l 

Device                 Boot        Start             End                        Blocks        Id     System
/dev/sda1            *             13319         13323                 32928+     e        W95 FAT16 (LBA)

#parted -l
number   Start              End                       Size                     Type                  File system      Flags
1                     110GB          110GB              33.7MB             primary           fat16                     boot, lba
```I tried to follow the instructions here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
but after I typed: 

find /boot/grub/stage1
I get: Error 15: File not found

The grub version in 0.97 as well, and a lot those steps appear to be for grub 2.

Would it help if I reinstalled ubuntu in its old 10GB partition? 

When I install it, at some point I should have to specify where its going. I'd install it over my old Ubuntu installation, and my windows partition should still be there. After I've installed ubuntu again, there will be a new grub that recognizes my windows loader, as well as the new Linux partition I created when I reinstalled Ubuntu. Would this work?

I'm sure there's a much better way, but at this point I'm starting to get scared of losing everything I have in  Windows. I'm willing to sacrifice all that I had in Linux (most of its  backed up anyway). I'd feel much more comfortable doing it like that...if it would work!

---

### Post by garvinrick4 on 2011-10-01
You will have to have a  linux live cd (install cd using Try) and run
a boot script that would tell all things about your system and its booting setup.
Is below. All other replys would now be a pure guess at best.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
Download to lets say Desktop and extract using archive manager and then run
this line of code below will put a  RESULTS file on desktop copy and paste to this thread.
```
sudo bash ~/Desktop/boot_info_script.sh
```

---

### Post by tomkat3 on 2011-10-01
```
sh-4.1# cat RESULTS.txt 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:   Syslinux looks at sector 7650 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *    213,958,656   214,024,512        65,857   e W95 FAT16 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1002 MB, 1002438656 bytes
31 heads, 62 sectors/track, 1018 cylinders, total 1957888 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     1,956,595     1,956,534   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       855bbeec-347d-4f3b-a944-a373353f9848   ext2       
/dev/sda1        5E51-6017                              vfat       LINUX
/dev/sdb1        15E4-3478                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)
/dev/loop1       /initrd/pup_ro1          ext2       (rw,noatime,errors=continue)
/dev/sdb1        /initrd/mnt/dev_save     vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,quiet,errors=remount-ro)


============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default puppy
display boot.msg
prompt 1
timeout 50

F1 boot.msg
F2 help.msg
F3 help2.msg

label puppy
kernel vmlinuz
append initrd=initrd.gz pmedia=usbflash
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.gz                                      1
            ?? = ??             vmlinuz                                        1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux.cfg                                   1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 02 10 00  |.X.MSWIN4.1.....|
00000010  02 00 02 00 00 f8 81 00  3f 00 ff 00 00 c0 c0 0c  |........?.......|
00000020  41 01 01 00 80 24 29 17  60 51 5e 4e 4f 20 4e 41  |A....$).`Q^NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 00 00  |ME    FAT16   ..|
00000040  80 00 29 17 60 51 5e 4e  4f 20 4e 41 4d 45 20 20  |..).`Q^NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

hda hdb hdc hdd sdc sdd sde sdf sdg sdh sdi 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

sh-4.1# 

```

---

### Post by garvinrick4 on 2011-10-01
Your 120 gig drive reported as sda drive has no operating system on it at all. I operating system has to be installed.
Here is the "how to" and download from Ubuntu. Sorry I cannot report better news.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
If you need anything further to assist you just post to this thread I will keep it subscribed
so will know when you post. Take care Tomkat3

---

### Post by tomkat3 on 2011-10-01
Ugh, how did I do that? Using test disk is less than intuitive...

Thanks for the help all the same. I'll look around to see if I can save somethings with Testdisk again. It doesn't look like I can make things any worse...

---

### Post by garvinrick4 on 2011-10-01
> Thanks for the help all the same.No problem at all you finish your education and prosper tomkat3.

---

### Post by tomkat3 on 2011-10-01
Ah-ha! I did it! I looked at the Testdisk tutorial here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

All I did was this: So I had a hunch that my grub was in that 32MB partition right? So in test disk, I simply switched some letters from D to L. Turns out D means 'deleted' (why does Testdisk automatically set every partition to 'deleted?!?) and L means logical, which means the computer knows it exists, or something like that.

The first time I used Testdisk I just looked at the results of the quick search, and I thought it would automatically fix everything. Then, without reading much of the fine print, I told it to 'write'. Everything was deleted. D'oh.

What fixed everything was this: I switched the letter of the 10GB Linux partition and the 32MB partition to L (running inside my PuppyLinux Live USB) and rebooted. Then grub appeared and I booted into Ubuntu! At least a partial victory! I then rebooted and tried to boot into Windows, and it said something like no such disk. A program I need for an engineering class creates save files upwards of 3MB in size that I hadn't backed up. I really needed to get in there

Then from my familiar old Ubuntu, I ran Testdisk again, this time I did a deeper search (since it didn't appear to be catching my 110GB Windows partition) and Testdisk suggested to me the stuff given in the attached picture. I wanted to make the 32MB partition an L, but everything turned grey when I did that, which probably means it wouldn't have worked. The important letter is the one to the far left. I changed it using the left and right arrow keys.

Dell Utility was *
My Vista partition (I upgraded from Vista to 7) was L
The 10GB Linux partition was L

I'm not sure what happened, but now everything appears to be back to normal!\\:D/ Turns out all I had to do was read the instructions! 

Anyone know of a good tutorial on how to expand my Linux partition like I wanted to in the first place?

---

### Post by oldfred on 2011-10-01
Great progress.

Expanding an Ubuntu System Partition and related info:
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

