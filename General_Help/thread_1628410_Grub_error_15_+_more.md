---
title: "Grub error 15 + more"
date: 2010-11-22
forum: General Help
---

### Post by Shanttu on 2010-11-22
Greetings community. I have been reading many, many posts here but have not written any. First time now and help is needed. 

OS is 10.10.
I did not make any radical change since my last working startup. When I booted, it gave error 15 so it did not make it to boot menu.

Gparted scans devices to infinity even if only one drive(?) dev/sda is selected
I tried Super Grub Disk. No luck. 

I began reinstalling Ubuntu with Live CD. Went to manual partitioning, deleted linux sections and added swap and root. Together 60 gb. 

When reinstalling it gives me error 
Input/output error during read on /dev/sda
Retry Ignore Cancel. 

I have Windows on another partition and I would like to save that.

Maybe I tried too much and fast for a beginner. I have n900 as a phone and Ubuntu on netbook and I really would like my main machine to work with Linux as well. Setting things up with thismachine has been very difficult. 

Any ideas how to continue? Big thanks for replies in advance.

---

### Post by oldfred on 2010-11-22
Grub error 15 is usually a old grub legacy and new grub2 not getting along error.

To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by Shanttu on 2010-11-23
Thank you for the reply. Here results

```
 File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   507,357,651   507,357,589   7 HPFS/NTFS
/dev/sda2         507,359,230   625,141,759   117,782,530   5 Extended
/dev/sda5         507,359,232   509,310,975     1,951,744  82 Linux swap / Solaris
/dev/sda6         509,313,024   625,141,759   115,828,736  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b3833064-5d51-460a-86ce-add8110e20dd   ext4                                     
/dev/sda1        98C0D0FCC0D0E194                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cb6e9649-43cb-464e-aa1e-72d1d9419b14   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff 
C:\wubildr.mbr = "Ubuntu" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d0 31 34 b5 cc 62 d4 fc  44 c9 be 5c 64 c8 53 ee  |.14..b..D..\d.S.|
00000010  81 63 f3 7a 23 5d 64 56  88 65 d9 0e 23 74 ef 0e  |.c.z#]dV.e..#t..|
00000020  85 3f 7f 79 14 4d 09 e8  ef 3b e9 3b 24 3b 6c dc  |.?.y.M...;.;$;l.|
00000030  ab 18 1e a6 4d a1 4b 4b  99 b0 5a 14 fb 2d 62 46  |....M.KK..Z..-bF|
00000040  89 fb f6 ee 37 ce 93 fd  69 d3 56 36 95 83 16 d4  |....7...i.V6....|
00000050  e7 ea ee 0a 7e 6f 77 35  29 fd d6 f9 d6 2b d7 42  |....~ow5)....+.B|
00000060  ea dc 89 0e ff 91 d3 1a  a3 01 9f 76 77 37 99 c3  |...........vw7..|
00000070  35 4d 97 b9 66 6d 7f 07  47 b7 c5 b8 6c e8 8f fd  |5M..fm..G...l...|
00000080  bb c9 3b a7 7f b8 c6 d8  c9 8c 41 22 67 97 d5 f6  |..;.......A"g...|
00000090  71 78 7d a9 4a 0f 11 fd  ff 95 2d 6f 25 19 dd cd  |qx}.J.....-o%...|
000000a0  c6 da 02 90 23 fa 9d 9c  b3 23 62 ce 29 e4 5f 67  |....#....#b.)._g|
000000b0  03 10 a7 f6 49 9c 8d c8  77 c5 09 ce 8f af ea 9c  |....I...w.......|
000000c0  6d 45 2d 32 a9 45 9d 33  79 87 7d ba be 38 29 e2  |mE-2.E.3y.}..8).|
000000d0  37 16 67 4f a9 ca d2 f7  24 33 dd 98 6f 3f 98 d1  |7.gO....$3..o?..|
000000e0  cd b2 91 0e b3 a6 46 7e  7f 27 50 3d 9e e3 0d ba  |......F~.'P=....|
000000f0  e5 bc 5c d3 63 1b ca b9  2a 77 67 f9 b7 ab 2f 85  |..\.c...*wg.../.|
00000100  85 23 5f df d6 bb 99 1b  ee c0 8f 29 eb 3a dd 67  |.#_........).:.g|
00000110  89 84 32 70 43 6d 9a af  ef ef b3 ac d6 10 f6 30  |..2pCm.........0|
00000120  98 84 21 e4 ff b3 f6 48  de 79 5e e6 ad 2c c6 dc  |..!....H.y^..,..|
00000130  ae b3 2d ce 4b b2 b6 94  8b 7b 5a 9e bc f8 82 b5  |..-.K....{Z.....|
00000140  26 97 0c 8c a6 77 f2 54  f9 5a 18 97 65 ee e6 82  |&....w.T.Z..e...|
00000150  ee cb 77 fd 9d b8 7b 87  80 a7 7d 7d 35 fd d8 cc  |..w...{...}}5...|
00000160  84 cd b6 88 f5 bc b1 6b  1f b9 9a 79 5a 43 02 3e  |.......k...yZC.>|
00000170  ca cb 96 5b bc 3f cc 98  32 87 fa 74 29 71 ca e7  |...[.?..2..t)q..|
00000180  39 06 6d dc 24 82 da e0  a7 ee e7 e7 07 7e b0 fd  |9.m.$........~..|
00000190  bf db eb dd df 68 d6 d3  5f 92 5b e4 b0 18 ad d7  |.....h.._.[.....|
000001a0  58 5b 5e bb c2 9f 6d a3  d0 62 ea dc 54 01 e0 83  |X[^...m..b..T...|
000001b0  a8 c1 bc 10 e0 c6 88 be  b3 36 58 32 b4 76 00 fe  |.........6X2.v..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  1d 00 00 70 e7 06 00 00  |...........p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by oldfred on 2010-11-23
You missed the top part of the script.

Were you using wubi and then installed. There are some known issues with wubi lately on grub installs.

Your install in sda6 has issues with sda6. One place in script shows it and the other cannot parse it. I would try fsck first on sda6.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda6
if errors:
sudo e2fsck -f -y -v /dev/sda6

---

### Post by Shanttu on 2010-11-23
I was wondering why that wubi was there cause I installed from CD. Weird. Here top, as a n00b I thought that was irrelevant. 

```
============================ Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk
```

---

### Post by oldfred on 2010-11-23
You have syslinux in the MBR. That is usually for USB flash drives?

You should have either grub2 or a windows boot loader. Grub will not install properly until you fix the issue with sda6. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You can install a windows style boot loader if you want to get windows working now.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

And you can install grub2 to the MBR but I do not think as long as sda6 has issues it will not work.

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda6 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by Shanttu on 2010-11-23
sudo e2fsck -C0 -p -f -v /dev/sda6

```
e2fsck: Bad magic number in super-block while trying to open /dev/sda6
/dev/sda6: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```sudo e2fsck -f -y -v /dev/sda6

```
e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
Is it possible to fix this with win xp install CD and try repair mode? If yes I'll try that one and reinstall Ubuntu.

---

### Post by oldfred on 2010-11-23
Windows does not even see Linux partitions. 

Did you try what it said in the alternate superblock? 
e2fsck -b 8193 /dev/sda6

There are many super blocks so sometimes you have to try others also.


If you are starting to have hard drive issues, you need to have good backups.

---

