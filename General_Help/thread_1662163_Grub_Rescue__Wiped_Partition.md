---
title: "Grub Rescue / Wiped Partition"
date: 2011-01-07
forum: General Help
---

### Post by Nuker90 on 2011-01-07
Hello,

I have a pretty ugly problem, I guess, and I really need your help, please.

I had Ubuntu 10.04 on my laptop, and updated to 11.04. For some reason, it didn't work anymore (after 5 mins, it was freezing) so I wanted to reinstall and get to 10.04 again (I installed it using Wubi, on Windows 7, separate partition). But there was no Ubuntu in the ADD/REMOVE list. Ok so I used a partition wizard to notice that the partition with Ubuntu was recognized as "Others" (not NTFS or anything), so I told the program to WIPE it, format it as NTFS and I was planning to reinstall Ubuntu 10.04 over there. But it seems like this was a big mistake - when I rebooted my laptop, I got the GRUB RESCUE console. 

Can someone please help me with this? I want to make it run again so I can get into my Windows 7 at least and to get to the Ubuntu 10.04. Please help me...


Thank you very much for your time,
Nuker90.

---

### Post by TeoBigusGeekus on 2011-01-07
To recover grub 2, follow [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") guide.

---

### Post by Nuker90 on 2011-01-07
Is this working even if my Ubuntu partition is (I think) empty now? 'cause I said I just WIPED it and FORMATED it... :s

---

### Post by TeoBigusGeekus on 2011-01-07
You could [remove grub2]("http://www.lukeaddison.com/removing-linux-grub-restoring-windows-7-boot-gui/").

---

### Post by Nuker90 on 2011-01-07
Thanks, this may seem to fix exactly my problem... but I don't have a Windows 7 DVD because my laptop came with it pre-installed, #@#! it! :(

---

### Post by TeoBigusGeekus on 2011-01-07
What I'd do if I were you:
I'd reinstall ubuntu (real installation, not a wubi one). After the installation, ubuntu would have reinstalled grub2 again.
In this way, I'd end up with both win7 and ubuntu correctly and properly recognized.

PS: A word of advice; stay away from alpha versions, unless of course you like adventures.
As a matter of fact, do not even install new ubuntu releases when they come out: first wait for a couple of months, so that the major bugs are more or less fixed.

---

### Post by wilee-nilee on 2011-01-07
> **Nuker90 said:**
> Thanks, this may seem to fix exactly my problem... but I don't have a Windows 7 DVD because my laptop came with it pre-installed, #@#! it! :(

Before you do anything more, and I can give you a link to a W7 recovery ISO down load do this. We should really see more of your setup to advise.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by Nuker90 on 2011-01-07
Ok that sounds good... can I do it if I burn the image on a CD, as instructed on the website? 'cause I've already started to burn the live CD.

@ This was for TeoBigusGeekus

@ wilee-nilee: I'll do that. Thanks.

---

### Post by wilee-nilee on 2011-01-07
> **Nuker90 said:**
> Ok that sounds good... can I do it if I burn the image on a CD, as instructed on the website? 'cause I've already started to burn the live CD.

@ This was for TeoBigusGeekus

@ wilee-nilee: I'll do that. Thanks.

Live cd is fine, as well for the script if you want to post it.

---

### Post by Nuker90 on 2011-01-07
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/burg.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSDOS5.0: Fat 16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    30,800,324    30,720,000   7 HPFS/NTFS
/dev/sda3          30,812,670   135,958,094   105,145,425   7 HPFS/NTFS
/dev/sda4         135,958,156   976,768,064   840,809,909   f W95 Ext d (LBA)
/dev/sda5         135,958,158   177,952,004    41,993,847  83 Linux
/dev/sda6         177,952,068   976,768,064   798,815,997   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 245     1,999,871     1,999,627   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        62424F38424F1069                       ntfs       RECOVERY                      
/dev/sda3        01CB67742DAD4AF0                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CBAEBBFF12CA50                       ntfs       Ubuntu                        
/dev/sda6        01CB677E605A9340                       ntfs       Vlad                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3B69-1AFD                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/3B69-1AFD         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5        /media/Ubuntu            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  63 95 cb f4 36 22 65 23  5b a4 b3 85 7f d3 c2 30  |c...6"e#[......0|
00000010  5a ff e6 b0 ef 37 6f 2b  3f fd df f3 f5 ff 57 5b  |Z....7o+?.....W[|
00000020  31 3e df a6 c9 fb a3 07  60 b4 75 5b da 4d 44 b2  |1>......`.u[.MD.|
00000030  a6 5a 6c 97 34 ec 87 ff  ff ff ff ff ff ff ff e0  |.Zl.4...........|
00000040  80 17 c1 5e a4 32 e8 11  32 50 d3 30 8c 3a 09 c8  |...^.2..2P.0.:..|
00000050  04 60 c4 9c e0 ac 20 e0  29 3b 22 14 08 c6 02 06  |.`.... .);".....|
00000060  80 be 80 51 83 94 00 49  18 bc 94 74 6c 69 88 e4  |...Q...I...tli..|
00000070  05 52 e2 38 8d 6d 71 d9  82 9f 99 fb af fb 4f 85  |.R.8.mq.......O.|
00000080  93 7b 39 d6 5f fc 31 bd  33 00 92 80 c0 ff 73 99  |.{9._.1.3.....s.|
00000090  53 61 3d 73 ff fb a0 60  a2 00 04 0c 68 cb 13 5a  |Sa=s...`....h..Z|
000000a0  2b 70 6e cc f9 93 67 22  6e 10 89 a1 2c 4d 6c ad  |+pn...g"n...,Ml.|
000000b0  c1 b7 90 25 c9 9d e5 28  2a ff 86 15 f9 ff 87 94  |...%...(*.......|
000000c0  e6 66 52 0e 77 ea 64 bd  57 42 8e f4 29 49 57 ca  |.fR.w.d.WB..)IW.|
000000d0  e8 a7 32 d8 d4 63 a2 be  45 aa 32 2f 3d 4b db ff  |..2..c..E.2/=K..|
000000e0  ff ff ff ff ff ff ee 40  c0 09 f0 51 16 59 42 65  |.......@...Q.YBe|
000000f0  96 5d d2 1d c7 80 1d 9e  16 1d e4 b4 c7 44 54 41  |.]...........DTA|
00000100  45 01 25 80 80 47 84 40  42 72 20 e9 34 ea ca c7  |E.%..G.@Br .4...|
00000110  06 09 a8 41 c1 b3 92 46  5f 20 9d 8c cb 6e 4b b1  |...A...F_ ...nK.|
00000120  87 47 4f 17 2a df c7 73  a5 99 af 40 14 20 88 2e  |.GO.*..s...@. ..|
00000130  76 c6 56 aa 7d 0e 3c d7  e7 bf be 04 14 2d 16 6b  |v.V.}.<......-.k|
00000140  de 38 53 b1 18 b8 43 a1  ae 52 0d bc 6b c4 b4 71  |.8S...C..R..k..q|
00000150  39 0f ff ff ff f2 20 00  06 e3 02 08 63 52 00 25  |9..... .....cR.%|
00000160  11 c1 b2 01 c8 64 d0 cc  40 dd 79 8c 63 03 d2 1c  |.....d..@.y.c...|
00000170  15 2a 9b ca 50 44 b6 23  92 fa 8f 60 0a 80 0d 5b  |.*..PD.#...`...[|
00000180  9f 18 79 6b c0 94 72 cc  ed de 81 44 6a c2 35 57  |..yk..r....Dj.5W|
00000190  ec b6 df fe 71 21 41 d2  ee 61 fa b5 d9 dc 73 bf  |....q!A..a....s.|
000001a0  fb fe db cf 3e 7b 3a 9c  b1 2b 43 51 40 14 66 c8  |....>{:..+CQ@.f.|
000001b0  aa 51 00 dd f5 56 5a 4e  8a 59 92 ad ba 19 00 fe  |.Q...VZN.Y......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 77 c6 80 02 00 fe  |..........w.....|
000001d0  ff ff 05 fe ff ff 79 c6  80 02 3c f7 9c 2f 00 00  |......y...<../..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```


Here it is. 


Thanks.

---

### Post by wilee-nilee on 2011-01-07
Something is not right the sda5 shows NTFS, and a Ubuntu stanza. I have the feeling your new at this no big deal.

You can reload the MS bootloader with this recovery link and the command highlighted. Boot the recovery cd choose the language then choose repair or press r I believe, get to the command line=terminal, and run this command.
```
bootrec.exe /fixmbr
```

This will put the MS bootloader back into windows then we can get you setup how you want.

---

### Post by Nuker90 on 2011-01-07
Ehm, sorry, but what recovery CD? and which recovery link?

---

### Post by wilee-nilee on 2011-01-07
> **Nuker90 said:**
> Ehm, sorry, but what recovery CD? and which recovery link?


Sorry my bad.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

My providers server went down right after I posted and forgot the link.

---

### Post by Nuker90 on 2011-01-08
Ok thank you very much, now I am in Windows 7 without any problem :)

So, next I should reinstall Ubuntu 10.04, right? Should I do it from the LiveCD or from Wubi.exe? Also, how can I do it so the GRUB won't replace the Windows7 booting manager (I want to keep Windows' booting manager just in case I encounter again the problems with Ubuntu and I'll be stuck again with GRUB).

---

### Post by wilee-nilee on 2011-01-08
> **Nuker90 said:**
> Ok thank you very much, now I am in Windows 7 without any problem :)

So, next I should reinstall Ubuntu 10.04, right? Should I do it from the LiveCD or from Wubi.exe? Also, how can I do it so the GRUB won't replace the Windows7 booting manager (I want to keep Windows' booting manager just in case I encounter again the problems with Ubuntu and I'll be stuck again with GRUB).

Boot the live Ubuntu cd, select try not install, and take a screen shot of the gparted partitioner. You have some inconsistencies in the script that are kind of hard to tell what is going on.

---

### Post by Nuker90 on 2011-01-09
Yeah, indeed something is wrong with the partitions because I can't see the 20GB's ("Ubuntu" named) partition in Windows Explorer. By the way, I used MiniTool Partition Wizard Home Edition 5.2 to make the partitions.

Here is the screenshot:

[IMG]http://img825.imageshack.us/img825/8449/screenshotqb.png[/IMG]

---

### Post by wilee-nilee on 2011-01-09
So do you want a dual boot that is partitioned or a Wubi. 

Can you identify if there is anything in the sda6 partition. It has a triangle on it right click that partition from gparted then information, and see what it says.

There is no partitioning done when installing a wubi.

---

### Post by Nuker90 on 2011-01-09
Ok, let me first explain what is with each of the partitions. 

The "OS" one is the C:\  - it has Windows 7 on it and that's all.
The "Ubuntu" one is an empty partition made for Ubuntu 10.04 (I used it before when I installed it via Wubi in there); now, I can't see this partition in Windows Explorer. Any idea why? When I boot in Ubuntu LiveCD, I can see it and it's empty. 
The "Vlad" one is actually the one that has the most stuff on it - it has all my files and everything not-related to the OS (Windows 7). It's my main partition for work files and everything like this. I don't know why it has that error sign; I attached below a screenshot of what you asked.



[IMG]http://img713.imageshack.us/img713/1475/screenshotjmi.png[/IMG]





What I want now:

I want to install Ubuntu 10.04 on the "Ubuntu" partition. I don't really care if it's via Wubi or via the LiveCD (I'd prefer to do it the best way, you tell me...). Also, if it's possible, I'd like to be able to see that partition ("Ubuntu") in the Windows Explorer (or to know why it is invisible). And one more thing, but I don't know if it's possible: can I keep the Windows booting manager instead of the GRUB one? Or what do you recommend me to do?

Thank you very much... :) And sorry for keeping your time.

Nuker90

---

### Post by wilee-nilee on 2011-01-09
So you can't see Ubuntu partitions from Widows, you can only dual boot it or a wubi install, both boot to the Ubuntu OS only. You could run Ubuntu in a virtual though is you want to have it available in a live windows environment.

You can access the Wubi and open it but not run it at the same time in windows.

You need to run a chkdsk /r on the vlad partition, have it backed up first though.

---

### Post by Nuker90 on 2011-01-10
So why can't I see that partition? I want to use it to install Ubuntu on it. It is currently empty (it has only the System Volume Information thingy - I wiped and formated it; it was the partition where my previous Ubuntu was and this wipe caused the problem with the booting in Windows). 

I want to install Ubuntu 10.04 in such a way so I will be prompted at the beginning of the booting to select Win7 / Ubuntu, just like it was before.

---

### Post by wilee-nilee on 2011-01-10
Your trying to customize your set up in a way that has left you in this state. You should of had the wubi in C and what is now the big partition=sda6 next to the Ubuntu should have just been a primary and would be D. You also look as though the sda6 needs a chkdsk /f/r run, but is inside a extended, which for me makes me wary to advise here.

Having a Wubi setup inside a extended partition and out of C is doable probably but to me looks more like a haphazard setup of wants or mistakes to be honest.:)

The problem here for you is that wubi although a nice try out method is not used by many users so getting help is sporadic if at all, and limited somewhat to the inherent problems. If this was a real dual boot you would off to the races, many more users are familiar with that.

I'm not a wubi user so I can really be of no more help good luck.

---

### Post by Nuker90 on 2011-01-18
Ok, I reinstalled Ubuntu via Wubi on the special-made-for-it partition and now I have 2 booting managers (because of the Windows one from C:\ and the Ubuntu one - Grub - from G:\), but it is ok... I'll just leave it like this for the moment as long as Windows & Ubuntu are working now :D


Thank you for your support.

Nuker90

---

### Post by Nuker90 on 2011-01-18
Sry for double post

---

