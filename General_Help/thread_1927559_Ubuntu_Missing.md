---
title: "Ubuntu Missing"
date: 2012-02-18
forum: General Help
---

### Post by delonicdevil on 2012-02-18
Dear all this is what happened. 

My laptop dual boots windows XP and Ubuntu 

I have parition the harddisk to give both OS  the same amount of space. 

Recently, my windows XP went cranky and I hard to reinstall it. 

After, I have reintsalled it, the harddisk, which was supposed to be partitioned into 2, got merged into 1 instead. However, the space in the harddisk indicates that only half of the space is available which led me to think that my ubuntu is still there somewhere. Also, the dual boot menu is missing. 

Can you anyone help me out?

---

### Post by raja.genupula on 2012-02-18
Hi look at my signature for bootinfoscript . boot to Ubuntu LIVE with a live CD and please post the output of that here . 

Thank you ,

---

### Post by gordintoronto on 2012-02-18
This is a common situation:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by delonicdevil on 2012-02-19
> **raja.genupula said:**
> Hi look at my signature for bootinfoscript . boot to Ubuntu LIVE with a live CD and please post the output of that here . 

Thank you ,
Here it is thank you!
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   100,550,834   100,550,772   7 NTFS / exFAT / HPFS
/dev/sda2         100,566,900   117,226,304    16,659,405   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2A04A1FF04A1CE5F                       ntfs       
/dev/sda2        3EC6-2E70                              vfat       PRESARIO_RP

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/2A04A1FF04A1CE5F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 74 87 fe 05  |........?...t...|
00000020  cd 33 fe 00 6e 3f 00 00  00 00 00 00 02 00 00 00  |.3..n?..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 70 2e c6 3e 20  20 20 20 20 20 20 20 20  |..)p..>         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Q-collective on 2012-02-19
Windows probably just overwrote the MBR. You may want to try out the [Boot Repair Disc](http://sourceforge.net/p/boot-repair-cd/home/Home/) to fix this.

---

### Post by delonicdevil on 2012-02-19
> **Q-collective said:**
> Windows probably just overwrote the MBR. You may want to try out the [Boot Repair Disc]("http://sourceforge.net/p/boot-repair-cd/home/Home/") to fix this.

Hi i tried it. But i was being prompted to connect to the internet. However, for some reason, i couldn't. is it essential to connect to the internet?

---

### Post by Mark Phelps on 2012-02-20
To use that, you either have to install the software, or you have to download the CD image file and burn the CD.  Either way, you have to get the stuff from their server -- which requires Internet access to do that.

---

### Post by delonicdevil on 2012-02-20
> **Mark Phelps said:**
> To use that, you either have to install the software, or you have to download the CD image file and burn the CD.  Either way, you have to get the stuff from their server -- which requires Internet access to do that.


Hi, I reread my previous post and i think that i might have misled you guys. =/

I did download the image file and burn the cd. 

I reach the boot-repair OS and when I click repair boot, there was a prompt to connect to the internet. I couldn't connect and so i just press ok when prompted to connect to the internet. 

Afterwhich, there was a progress bar showing boot repair in progress. Afterwhich, i got text report and a notification that says its done. however, it didn't solve the problem. 

I hope i make sense now? =D

---

### Post by Mark Phelps on 2012-02-21
You said Boot-Repair didn't work, so can you not even boot XP now?

There are not two equally sized partitions, only a real large one and a real small one.

There's no indication I see in the script results indicating that Ubuntu is installed on your PC.

---

