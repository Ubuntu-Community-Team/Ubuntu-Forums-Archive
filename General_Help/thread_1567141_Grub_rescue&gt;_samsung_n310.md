---
title: "Grub rescue&gt; samsung n310"
date: 2010-09-03
forum: General Help
---

### Post by camoledge on 2010-09-03
[COLOR="Black"][/COLOR]Hello everybody I hope I get some support for this problem because it is really driving me crazy.
After Installing the latest Ubuntu Netbook Remix yesterday an trying to boot it from an SD drive without succes I had the stupid idea of setting up as startup PENDRIVE the D: partition of my Hard Disk. You know the "classic" empty D: partition of an XP OS. I restarted my PC and got to try Ubuntu...still I was pretty worried by the fact that my computer had booted directly to the Ubuntu trial version. After testing it while installing the dual boot version I would have then used came the problems, I personally don't know if I clicked something wrong because I think I followed all the right steps, still all I get right now is this page.

```
 error: no such device: b26dd508-c663-4c85-ad14-9b914f2777al.
grub rescue> 
```

I' ve tried to find out what I coould about it entering "ls".

As I knew I got just one hd, divided in three partitions.

```
 (hd0) (hd0,3) (hd0,2) (hd0,1) 
```

then "set"

```
 prefix=(hd0,1)/boot/grub
root=hd0,1 
```

Right now I am writing you from my gf's MacBook, so I don't even have something with XP on close, even if I might get my hands on it during the afternoon...

I tried to search this forum, tried every process listed, but at some point I get the unknown filesystem error everytime.

I need my PC back badly and all the data on it, anyway next time I'm gonna think thrice before I try to mess up with Ubuntu again, before I need a programming class, at least...

---

### Post by camoledge on 2010-09-03
Even tried to set up my WD external hard drive as primary boot option after downloading xp on it...not working...

---

### Post by malangaman on 2010-09-03
Have you tried checking your BIOS set-up? I had a similar problem recently and it turned out that grub and BIOS referred to the drive with different names such as you are getting. See if the BIOS is recognizing your drive.

---

### Post by drs305 on 2010-09-03
If you would download and run meierfra's boot info script from the following link we will know the status of your system. 

Copy the contents of RESULTS.txt here, then highlight and press the # icon in the post's menubar  to generate "code" tags (for formatting it properly).

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by camoledge on 2010-09-03
> **malangaman said:**
> Have you tried checking your BIOS set-up? I had a similar problem recently and it turned out that grub and BIOS referred to the drive with different names such as you are getting. See if the BIOS is recognizing your drive.
That's what I get:

grub rescue> ls 

(hd0) (hdo,3) (hd0,2) (hd0,1) (hd1) (hd1,1)

BIOS

[Boot pririty order]

1. USB HDD  :  WD 5000EV External
2. IDE HDD  :  Hitachi HTS543216L9A300

I put them in this order to boot the external HD first.

I don't know, maybe downolading XP to my external HD doesn't mean that it can boot from there, I have also a samsung recovery CD and maybe I will be able to boot from cd soon, a friend is bringing me an external CD drive to connect via USB.
I feel so ashemed of having been such a dummy, a should have been reading about the bugs and problemss of Ubuntu Netbook Remix before doing anything. 
Anyway if you know a way to just restore everithing, like wiping away all data to have my main Hard Drive back, I'll gladly do it. I repeat I just want to be able to use my machine again, don't care about losing data.

---

### Post by camoledge on 2010-09-03
> **drs305 said:**
> If you would download and run meierfra's boot info script from the following link we will know the status of your system. 

Copy the contents of RESULTS.txt here, then highlight and press the # icon in the post's menubar  to generate "code" tags (for formatting it properly).

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Ehm, sorry for being such a dummy, but the only working computer right now available for me is the MacBook I am using. Can I download Boot Infoscript with it to my external HD? 

And then connect it to my Not Working-grub rescue> stuck PC? Drs305, I also took a llok at other similar threads where you gave useful answers about similar problems and even tried to follow the steps you suggested. 

But no way I get to boot something. If there was a way to just wipe away everything from the Hard Drives and Install XP from new...

Anyway trying to follow the rules of the forum that is what i get if I doot my computer with the default setting of the BIOS.

```
 error: no such device:  b26dd508- c663-4c85-ad14-9b914f2777a1
grub rescue> 
```

---

### Post by wilee-nilee on 2010-09-03
> **drs305 said:**
> If you would download and run meierfra's boot info script from the following link we will know the status of your system. 

Copy the contents of RESULTS.txt here, then highlight and press the # icon in the post's menubar  to generate "code" tags (for formatting it properly).

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

+1 as suggested by myself in another thread and this person post the script.

OP you are lucky to have this persons interest as in this area they are quite knowledgeable.

---

### Post by camoledge on 2010-09-03
> **wilee-nilee said:**
> +1 as suggested by myself in another thread and this person post the script.

OP you are lucky to have this persons interest as in this area they are quite knowledgeable.

I hope you both help me, and thanks for starting to take care of my problem. I would really like to test *bootinfoscript* but I don't know how to install it on my external hd using a Mac and don'tknow how it could be run from my stuck n310. that isn't able to go past the 
```
 grub rescue> 
```

stage.

---

### Post by wilee-nilee on 2010-09-03
The bootscript is not installed. It is downloaded using a Ubuntu environment; a live cd or running session. You then run a command in the terminal and it gives you a read out, in the text format of information that you would post in a reply, in code tags.

---

### Post by camoledge on 2010-09-03
> **wilee-nilee said:**
> The bootscript is not installed. It is downloaded using a Ubuntu environment; a live cd or running session. You then run a command in the terminal and it gives you a read out, in the text format of information that you would post in a reply, in code tags.

Again sorry for not understanding much out of it, as it is now you say I am going to be able to open a terminal on my N310. I don't know how to do it but I will try to find out how to do it. Right now anyway I am downloading ubuntu 10.04 netbook remixwith another netbook I will then try to make my SD my bootable device and run ubuntu from there on my N310. The fact is I don't have a USB stick right now. 

Another question, if I buy let's say Windows 7 and try to boot it from a CD drive on my messed up netbook will it install? I am up to pay for it to save time. But I would like to be 100% it is going to work before spending that much money.

---

### Post by wilee-nilee on 2010-09-03
> **camoledge said:**
> Again sorry for not understanding much out of it, as it is now you say I am going to be able to open a terminal on my N310. I don't know how to do it but I will try to find out how to do it. Right now anyway I am downloading ubuntu 10.04 netbook remixwith another netbook I will then try to make my SD my bootable device and run ubuntu from there on my N310. The fact is I don't have a USB stick right now. 

Another question, if I buy let's say Windows 7 and try to boot it from a CD drive on my messed up netbook will it install? I am up to pay for it to save time. But I would like to be 100% it is going to work before spending that much money.

So, you boot the live cd of ubuntu on a thumb however you want. you go to the link in my signature and download the script it will go to the downloads folder, drag the script to the desktop and run this command in a terminal. The terminal is in the menu.
```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create another file on your live cd desktop open it copy the text post it in a reply highlight it and click on the # in the reply panel.

To be honest since we know nothing of whats going on, or whats on your computer this script will clear up a lot of stuff for us to know.

---

### Post by camoledge on 2010-09-03
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2          12,594,960   260,147,199   247,552,240   7 HPFS/NTFS
/dev/sda3    *    260,147,200   308,496,194    48,348,995   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E48CF8E48CF8B262                       ntfs       RECOVERY                      
/dev/sda2        F658FA4858FA0761                       ntfs                                     
/dev/sda3        2441-31E8                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EABA-2E87                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda3        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=4 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu Netbook" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


```

Finally!

Now let's get down to work. 

I'll wait for you to guide me. Thanks for helping for now. You've been very kind and patient. And well, my machine at least is working booting from usb, so it's alive. :)

---

### Post by wilee-nilee on 2010-09-03
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 
This is the main problem, grub has been installed in the place of the MS bootloader in the MBR.

You can fix this a couple of ways the best being I think from a XP disc, here is a link to a ISO that you can burn.

I don't know if you have a usb dvd/cd reader for this netbook. Here are some links.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Just read the second link the fixmbr command will get you XP back for now, I'm not sure of how to get the wubi/Ubuntu install up and running. 

You mentioned W7 you can download a program from MS that will let you know if it will run, you want at least 2 gigs of ram for the 32 bit version of W7. I have a d250 acer aspireone with a atom chip and 2 gigs of ram W7; runs as fast as Ubuntu.

As your hard drive is now you could actually do a real dualboot not a install inside of Windows, this method is the preferred way to run the OS. The problems your having now would never have happened with a install from the booted Ubuntu cd done correctly.

You probably will need to put the boot flag on sda2 with gparted from the live Ubuntu cd I think as well to make it active. There is a boot in sda1 but it looks more like a previous install, or recovery, you would know better.

---

### Post by camoledge on 2010-09-04
I tried to burn the iso from the link on a cd with nero and then booting from the cd but I got the

```
 error: no such device; lots of numbers
grub rescue> 
``` screen again...

---

### Post by drs305 on 2010-09-04
> **camoledge said:**
> I tried to burn the iso from the link on a cd with nero and then booting from the cd but I got the

```
 error: no such device; lots of numbers
grub rescue> 
``` screen again...

Are you sure your computer is trying to boot the LiveCD first? Do you hear it spin up as the computer boots.

The BIOS has to be set to allow the CD to boot first - otherwise your computer will most likely boot from one of the hard drives. You have to enter the system BIOS during the initial power up and change the boot option to boot first from the CD. Which key to press to enter the BIOS setup varies by manufacturer - it is normally the DEL, ESC or one of the F (function keys). The monitor may (briefly) display which key to press to enter the BIOS setup screen.

---

### Post by camoledge on 2010-09-04
Yep, sure of it, already tried that. Maybe instead of a "real" CD I burned the ISO on with NERO, I should try to use a USB stick, does it make sense? Should I try that way? Isn't there a way to just cancel grub from the hard drive where XP is so that it boots again?

Or should I try as meierfra explains here?

[http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys](http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys)

---

### Post by camoledge on 2010-09-04
I actually tried to do the meierfra process, and also did same putting mbr instead of ms-sys as I was reading in another forum.

Still booting my netbook without my Live CD where Ubuntu Netbook Remix is I can not enter XP.

Still instead of the ```
 grub rescue> 
``` page now I get another scree booting my netbook without anything plugged in ```
 MBR 1234FA: 
``` from there even pressing 1 as I've been reading in many forums I can't go anywhere nor type anything

Anyway if this could add info...

```
 To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e6a11c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    12594959     6297448+  12  Compaq diagnostics
/dev/sda2        12594960   260147199   123776120    7  HPFS/NTFS
/dev/sda3   *   260147200   308496194    24174497+   c  W95 FAT32 (LBA)
/dev/sda4               0           0           0    0  Empty

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7827455     3909696    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 
```

I then ran bootinfoscript again:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2          12,594,960   260,147,199   247,552,240   7 HPFS/NTFS
/dev/sda3    *    260,147,200   308,496,194    48,348,995   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EABA-2E87                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b6 07 ff 75 04 88  16 b6 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 b2 07 83 ee 10 d0  e8 73 f0 cd 1a 89 16 00  |.........s......|
00000040  08 e8 33 01 81 3e b4 07  ff ff 74 46 f6 06 b3 07  |..3..>....tF....|
00000050  80 74 06 b4 01 cd 16 75  39 f6 06 b3 07 40 74 07  |.t.....u9....@t.|
00000060  f6 06 17 04 0f 75 2b 31  c0 cd 1a 2b 16 00 08 2b  |.....u+1...+...+|
00000070  16 b4 07 72 d7 a0 b3 07  24 07 3c 07 75 0b be be  |...r....$.<.u...|
00000080  07 b0 00 b9 04 00 80 3c  00 75 66 fe c0 83 c6 10  |.......<.uf.....|
00000090  e2 f4 e8 e2 00 b4 0e be  a0 07 8a 0e b2 07 ac d0  |................|
000000a0  e9 73 02 cd 10 08 c9 75  f5 b0 3a cd 10 31 c0 cd  |.s.....u..:..1..|
000000b0  16 3c 00 74 f8 3c 0d 74  bc 3c 61 72 06 3c 7a 77  |.<.t.<.t.<ar.<zw|
000000c0  02 2c 20 88 c3 be a0 07  8a 0e b2 07 ac d0 e9 73  |., ............s|
000000d0  04 38 c3 74 06 08 c9 75  f3 eb d2 b8 0d 0e 31 db  |.8.t...u......1.|
000000e0  cd 10 8d 84 5f 00 3c 07  75 07 b0 1f a2 b2 07 eb  |...._.<.u.......|
000000f0  a1 e8 83 00 31 d2 b9 01  00 3c 04 74 11 73 f0 30  |....1....<.t.s.0|
00000100  e4 b1 04 d2 e0 be be 07  01 c6 8a 16 b6 07 bf 05  |................|
00000110  00 56 f6 c2 80 74 2b b4  41 bb aa 55 52 cd 13 5a  |.V...t+.A..UR..Z|
00000120  5e 56 72 1e 81 fb 55 aa  75 18 f6 c1 01 74 13 8b  |^Vr...U.u....t..|
00000130  44 08 8b 5c 0a be 90 07  89 44 08 89 5c 0a b4 42  |D..\.....D..\..B|
00000140  eb 0c 8a 74 01 8b 4c 02  b8 01 02 bb 00 7c 50 c6  |...t..L......|P.|
00000150  06 92 07 01 cd 13 58 5e  73 05 4f 75 b4 eb 90 81  |......X^s.Ou....|
00000160  3e fe 7d 55 aa 75 f6 31  db b8 0d 0e cd 10 b0 0a  |>.}U.u.1........|
00000170  cd 10 ea 00 7c 00 00 50  b8 0d 0e 31 db cd 10 be  |....|..P...1....|
00000180  8c 07 b9 04 00 ac cd 10  e2 fb 58 c3 4d 42 52 20  |..........X.MBR |
00000190  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000001a0  31 32 33 34 46 00 00 41  4e 44 54 6d 62 72 00 02  |1234F..ANDTmbr..|
000001b0  00 02 90 c7 12 00 80 00  00 00 00 00 a8 01 20 63  |.............. c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b6 07 ff 75 04 88  16 b6 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 b2 07 83 ee 10 d0  e8 73 f0 cd 1a 89 16 00  |.........s......|
00000040  08 e8 33 01 81 3e b4 07  ff ff 74 46 f6 06 b3 07  |..3..>....tF....|
00000050  80 74 06 b4 01 cd 16 75  39 f6 06 b3 07 40 74 07  |.t.....u9....@t.|
00000060  f6 06 17 04 0f 75 2b 31  c0 cd 1a 2b 16 00 08 2b  |.....u+1...+...+|
00000070  16 b4 07 72 d7 a0 b3 07  24 07 3c 07 75 0b be be  |...r....$.<.u...|
00000080  07 b0 00 b9 04 00 80 3c  00 75 66 fe c0 83 c6 10  |.......<.uf.....|
00000090  e2 f4 e8 e2 00 b4 0e be  a0 07 8a 0e b2 07 ac d0  |................|
000000a0  e9 73 02 cd 10 08 c9 75  f5 b0 3a cd 10 31 c0 cd  |.s.....u..:..1..|
000000b0  16 3c 00 74 f8 3c 0d 74  bc 3c 61 72 06 3c 7a 77  |.<.t.<.t.<ar.<zw|
000000c0  02 2c 20 88 c3 be a0 07  8a 0e b2 07 ac d0 e9 73  |., ............s|
000000d0  04 38 c3 74 06 08 c9 75  f3 eb d2 b8 0d 0e 31 db  |.8.t...u......1.|
000000e0  cd 10 8d 84 5f 00 3c 07  75 07 b0 1f a2 b2 07 eb  |...._.<.u.......|
000000f0  a1 e8 83 00 31 d2 b9 01  00 3c 04 74 11 73 f0 30  |....1....<.t.s.0|
00000100  e4 b1 04 d2 e0 be be 07  01 c6 8a 16 b6 07 bf 05  |................|
00000110  00 56 f6 c2 80 74 2b b4  41 bb aa 55 52 cd 13 5a  |.V...t+.A..UR..Z|
00000120  5e 56 72 1e 81 fb 55 aa  75 18 f6 c1 01 74 13 8b  |^Vr...U.u....t..|
00000130  44 08 8b 5c 0a be 90 07  89 44 08 89 5c 0a b4 42  |D..\.....D..\..B|
00000140  eb 0c 8a 74 01 8b 4c 02  b8 01 02 bb 00 7c 50 c6  |...t..L......|P.|
00000150  06 92 07 01 cd 13 58 5e  73 05 4f 75 b4 eb 90 81  |......X^s.Ou....|
00000160  3e fe 7d 55 aa 75 f6 31  db b8 0d 0e cd 10 b0 0a  |>.}U.u.1........|
00000170  cd 10 ea 00 7c 00 00 50  b8 0d 0e 31 db cd 10 be  |....|..P...1....|
00000180  8c 07 b9 04 00 ac cd 10  e2 fb 58 c3 4d 42 52 20  |..........X.MBR |
00000190  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000001a0  31 32 33 34 46 00 00 41  4e 44 54 6d 62 72 00 02  |1234F..ANDTmbr..|
000001b0  00 02 90 c7 12 00 80 00  00 00 00 00 a8 01 63 6f  |..............co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda3

00000000  fc 31 c0 8e d0 31 e4 8e  d8 8e c0 be 00 7c bf 00  |.1...1.......|..|
00000010  06 b9 00 01 f3 a5 be ee  07 b0 08 ea 20 06 00 00  |............ ...|
00000020  80 3e b6 07 ff 75 04 88  16 b6 07 80 3c 00 74 04  |.>...u......<.t.|
00000030  08 06 b2 07 83 ee 10 d0  e8 73 f0 cd 1a 89 16 00  |.........s......|
00000040  08 e8 33 01 81 3e b4 07  ff ff 74 46 f6 06 b3 07  |..3..>....tF....|
00000050  80 74 06 b4 01 cd 16 75  39 f6 06 b3 07 40 74 07  |.t.....u9....@t.|
00000060  f6 06 17 04 0f 75 2b 31  c0 cd 1a 2b 16 00 08 2b  |.....u+1...+...+|
00000070  16 b4 07 72 d7 a0 b3 07  24 07 3c 07 75 0b be be  |...r....$.<.u...|
00000080  07 b0 00 b9 04 00 80 3c  00 75 66 fe c0 83 c6 10  |.......<.uf.....|
00000090  e2 f4 e8 e2 00 b4 0e be  a0 07 8a 0e b2 07 ac d0  |................|
000000a0  e9 73 02 cd 10 08 c9 75  f5 b0 3a cd 10 31 c0 cd  |.s.....u..:..1..|
000000b0  16 3c 00 74 f8 3c 0d 74  bc 3c 61 72 06 3c 7a 77  |.<.t.<.t.<ar.<zw|
000000c0  02 2c 20 88 c3 be a0 07  8a 0e b2 07 ac d0 e9 73  |., ............s|
000000d0  04 38 c3 74 06 08 c9 75  f3 eb d2 b8 0d 0e 31 db  |.8.t...u......1.|
000000e0  cd 10 8d 84 5f 00 3c 07  75 07 b0 1f a2 b2 07 eb  |...._.<.u.......|
000000f0  a1 e8 83 00 31 d2 b9 01  00 3c 04 74 11 73 f0 30  |....1....<.t.s.0|
00000100  e4 b1 04 d2 e0 be be 07  01 c6 8a 16 b6 07 bf 05  |................|
00000110  00 56 f6 c2 80 74 2b b4  41 bb aa 55 52 cd 13 5a  |.V...t+.A..UR..Z|
00000120  5e 56 72 1e 81 fb 55 aa  75 18 f6 c1 01 74 13 8b  |^Vr...U.u....t..|
00000130  44 08 8b 5c 0a be 90 07  89 44 08 89 5c 0a b4 42  |D..\.....D..\..B|
00000140  eb 0c 8a 74 01 8b 4c 02  b8 01 02 bb 00 7c 50 c6  |...t..L......|P.|
00000150  06 92 07 01 cd 13 58 5e  73 05 4f 75 b4 eb 90 81  |......X^s.Ou....|
00000160  3e fe 7d 55 aa 75 f6 31  db b8 0d 0e cd 10 b0 0a  |>.}U.u.1........|
00000170  cd 10 ea 00 7c 00 00 50  b8 0d 0e 31 db cd 10 be  |....|..P...1....|
00000180  8c 07 b9 04 00 ac cd 10  e2 fb 58 c3 4d 42 52 20  |..........X.MBR |
00000190  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000001a0  31 32 33 34 46 00 00 41  4e 44 54 6d 62 72 00 02  |1234F..ANDTmbr..|
000001b0  00 02 90 c7 12 00 80 00  00 00 00 00 a8 01 de 66  |...............f|
000001c0  8f 06 78 00 be e7 7d ac  20 c0 74 09 b4 0e bb 07  |..x...}. .t.....|
000001d0  00 cd 10 eb f2 98 cd 16  cd 19 eb fe 3b 2e fc 7d  |............;..}|
000001e0  76 04 8b 2e fc 7d c3 42  6f 6f 74 20 65 72 72 6f  |v....}.Boot erro|
000001f0  72 0d 0a 00 00 00 00 00  d0 5c 00 00 7f 00 55 aa  |r........\....U.|
00000200


```

---

### Post by varunendra on 2010-09-04
> **camoledge said:**
> Yep, sure of it, already tried that. Maybe instead of a "real" CD I burned the ISO on with NERO, I should try to use a USB stick, does it make sense? Should I try that way? Isn't there a way to just cancel grub from the hard drive where XP is so that it boots again?

Or should I try as meierfra explains here?

[http://members.iinet.net.au/~herman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys]("http://members.iinet.net.au/%7Eherman546/p18.html#Replace_GRUB_in_MBR_with_ms-sys")

Burning ISO using Nero:
[http://johnbokma.com/mexit/2007/01/05/burning-dvd-iso-image-with-nero-express.html](http://johnbokma.com/mexit/2007/01/05/burning-dvd-iso-image-with-nero-express.html)

---

### Post by drs305 on 2010-09-04
Looking at the new results.txt the first thing I noticed was that your Windows partition doesn't have the "boot" flag set (which can be done via LiveCD's System, Administration, Disk Utility). The boot flag must be set properly for Windows to work.

However, you now have bigger problems that need to be addressed. Your initial RESULTS.txt showed this, which displayed a generally intact Windows install (but with Grub installed in the MBR):
> 
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk



Notice that whatever you have done has now wiped this information out:
> 
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''


So you are going to have to get that info restored. A Windows recovery program may be able to do it, or a linux app called Test Disk, but once you combine Windows stuff with Test Disk matters I'm not knowledgeable enough to help out.

Wait for someone else to reply, or start a new thread about how to restore disk information and include a link to this post and what you did that wiped out the partition information (if you know).

In the meantime, try not to write anything to the drive so that the information that still exists is not overwritten.

---

### Post by camoledge on 2010-09-04
Anyone there?

---

### Post by wilee-nilee on 2010-09-04
> **camoledge said:**
> Anyone there?

I would look at post 19 and ask questions if you don't understand, and maybe as suggested a new thread on restoring the XP portion or getting it to show.

---

### Post by camoledge on 2010-09-04
> **wilee-nilee said:**
> I would look at post 19 and ask questions if you don't understand, and maybe as suggested a new thread on restoring the XP portion or getting it to show.

I took a look, at posts 18 and 19 I will try to burn another CD with a Windows XP iso to see if I can fix things I messed up. As for the new thread it's already active but I got no answers until now. I tried to run testdisk but it wasn't able to retrieve any information or fix anithing.  

here is a link to my thread about how to fix my XP portion of the HD

[http://ubuntuforums.org/showthread.php?t=1567993](http://ubuntuforums.org/showthread.php?t=1567993)

---

### Post by camoledge on 2010-09-05
I am seriously getting frustrated by the outcome of every move I make to get my XP back. I tried to use testdisk (by the way sometimes E: is not able to find it and install it when I reebot from my USB Live CD), followed with attention the step by step instructions and finally after analyzing all the partitions of my Hard Drive decided to leave just the one that among its files had WINDOWS, making it bootable.

Leaving with D the messed up second partition and a third one almost empty partition (that only showed a line among its files, precisely "grub").

Saw green and thought this was the finally right configuration. Followed the next steps, restarted my computer and result was. BLANK SCREEN. If I press "Enter" something like a smiling face appears to me, my machine making fun of me probably.

Booted again from live CD ran bootinfoscript, and, it's a mess:  

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       247552239 sectors, but according to the info from 
                       fdisk, it has 247561649 sectors.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     12,594,960   260,156,609   247,561,650   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07B306F64674FFFF                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EABA-2E87                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/07B306F64674FFFF  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  fc 31 c0 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.1.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 10 2f c0 00  |........?..../..|
00000020  00 00 00 00 ff 75 04 88  ef 58 c1 0e 00 00 00 00  |.....u...X......|
00000030  00 00 0c 00 00 00 00 00  67 11 27 00 00 00 00 00  |........g.'.....|
00000040  f6 00 00 00 01 00 00 00  ff ff 74 46 f6 06 b3 07  |..........tF....|
00000050  00 00 00 00 01 cd 16 75  39 f6 06 b3 07 40 74 07  |.......u9....@t.|
00000060  f6 06 17 04 0f 75 2b 31  c0 cd 1a 2b 16 00 08 2b  |.....u+1...+...+|
00000070  16 b4 07 72 d7 a0 b3 07  24 07 3c 07 75 0b be be  |...r....$.<.u...|
00000080  07 b0 00 b9 04 00 80 3c  00 75 66 fe c0 83 c6 10  |.......<.uf.....|
00000090  e2 f4 e8 e2 00 b4 0e be  a0 07 8a 0e b2 07 ac d0  |................|
000000a0  e9 73 02 cd 10 08 c9 75  f5 b0 3a cd 10 31 c0 cd  |.s.....u..:..1..|
000000b0  16 3c 00 74 f8 3c 0d 74  bc 3c 61 72 06 3c 7a 77  |.<.t.<.t.<ar.<zw|
000000c0  02 2c 20 88 c3 be a0 07  8a 0e b2 07 ac d0 e9 73  |., ............s|
000000d0  04 38 c3 74 06 08 c9 75  f3 eb d2 b8 0d 0e 31 db  |.8.t...u......1.|
000000e0  cd 10 8d 84 5f 00 3c 07  75 07 b0 1f a2 b2 07 eb  |...._.<.u.......|
000000f0  a1 e8 83 00 31 d2 b9 01  00 3c 04 74 11 73 f0 30  |....1....<.t.s.0|
00000100  e4 b1 04 d2 e0 be be 07  01 c6 8a 16 b6 07 bf 05  |................|
00000110  00 56 f6 c2 80 74 2b b4  41 bb aa 55 52 cd 13 5a  |.V...t+.A..UR..Z|
00000120  5e 56 72 1e 81 fb 55 aa  75 18 f6 c1 01 74 13 8b  |^Vr...U.u....t..|
00000130  44 08 8b 5c 0a be 90 07  89 44 08 89 5c 0a b4 42  |D..\.....D..\..B|
00000140  eb 0c 8a 74 01 8b 4c 02  b8 01 02 bb 00 7c 50 c6  |...t..L......|P.|
00000150  06 92 07 01 cd 13 58 5e  73 05 4f 75 b4 eb 90 81  |......X^s.Ou....|
00000160  3e fe 7d 55 aa 75 f6 31  db b8 0d 0e cd 10 b0 0a  |>.}U.u.1........|
00000170  cd 10 ea 00 7c 00 00 50  b8 0d 0e 31 db cd 10 be  |....|..P...1....|
00000180  8c 07 b9 04 00 ac cd 10  e2 fb 58 c3 4d 42 52 20  |..........X.MBR |
00000190  10 00 01 00 00 7c 00 00  00 00 00 00 00 00 00 00  |.....|..........|
000001a0  31 32 33 34 46 00 00 41  4e 44 54 6d 62 72 00 02  |1234F..ANDTmbr..|
000001b0  00 02 90 c7 12 00 80 00  00 00 00 00 a8 01 63 6f  |..............co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

```I would like to run again testdisk right now but I don't know why sometimes I am able to do it sometimes I get this:

```
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/ lucid/restricted Translation-en_US
Hit http://archive.ubuntu.com lucid Release.gpg                                                         
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                      
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Hit http://archive.ubuntu.com lucid Release    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ 

 
```Disk Utilty shows me my 160 GB ATA Hitachi Hard Drive divided in 3.

A frist free section of 6.4 GB, a central NTFS section of 127GB flagged as bootable, a final 27 GB free section.

It then see my Verbatim Store N FAT 4GB (from where I boot)

And 691MB filesystem I don'tunderstand if it is the Ubuntu OS in the Pendrive that appears as standalone device.

In Ubuntu still, in the files and folders section, where I used to see two volumes one 160 GB and the Pendrive, now I only see a 127 GB Volume (corresponding to the bootable part of the hard drive).

Sorry for the long post.

Wouldn't that be possible (since anyway I like it a lot) to just format my Hard Drive and then (it would become empty right? As new?) install Ubuntu Netbook Remix there from my USB? I am not able to use a Windows XP restore CD, tried to burn ISOs without good outcome and I just would like to get rid of this USB stick all the time connected to my netbook...

---

### Post by camoledge on 2010-09-05
I was able to run testdisk again...just tell me what should I do please.

```
 TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS            784   0  1 16193 254 63  247561650
D FAT32 LBA            16193 105 41 19202 254 63   48348995 [PENDRIVE]
* FAT12                19203   0  1 19203 254 63      16065 

"list of files in the first partition"   

HPFS - NTFS            784   0  1 16193 254 63  247561650
Directory /

dr-xr-xr-x     0     0         0 16-Feb-2010 18:03 .
dr-xr-xr-x     0     0         0 16-Feb-2010 18:03 ..
dr-xr-xr-x     0     0         0  3-Sep-2010 14:50 .Trash-999
dr-xr-xr-x     0     0         0  2-May-2010 18:55 018e7103660af21bc4b5
dr-xr-xr-x     0     0         0 22-May-2009 03:54 Documents and Settings
dr-xr-xr-x     0     0         0 22-May-2009 11:06 Intel
dr-xr-xr-x     0     0         0 14-Feb-2010 14:24 MSOCache
dr-xr-xr-x     0     0         0 29-Aug-2010 11:45 PFiles
dr-xr-xr-x     0     0         0 22-May-2009 03:55 Program Files
dr-xr-xr-x     0     0         0 22-May-2009 11:50 RECYCLER
dr-xr-xr-x     0     0         0 22-May-2009 03:54 System Volume Information
dr-xr-xr-x     0     0         0 14-Feb-2010 16:50 Temp
dr-xr-xr-x     0     0         0 22-May-2009 03:48 WINDOWS


"list of files in the second partition"

     FAT32 LBA            16193 105 41 19202 254 63   48348995 [PENDRIVE]
Directory /

-r-xr-xr-x     0     0     15218  2-Sep-2010 20:47 LDLINUX.SYS
drwxr-xr-x     0     0         0  2-Sep-2010 20:47 System Volume Information
drwxr-xr-x     0     0         0 29-Apr-2010 14:12 .disk
-rwxr-xr-x     0     0       229 29-Apr-2010 14:12 README.diskdefines
-rwxr-xr-x     0     0       151 29-Apr-2010 14:12 AUTORUN.INF
drwxr-xr-x     0     0         0  3-Sep-2010 23:07 CASPER
drwxr-xr-x     0     0         0 29-Apr-2010 14:12 DISTS
drwxr-xr-x     0     0         0 29-Apr-2010 14:12 INSTALL
drwxr-xr-x     0     0         0 29-Apr-2010 14:12 SYSLINUX
-rwxr-xr-x     0     0      5465 29-Apr-2010 14:12 MD5SUM.TXT
drwxr-xr-x     0     0         0 29-Apr-2010 14:12 PICS
drwxr-xr-x     0     0         0 29-Apr-2010 14:12 POOL
drwxr-xr-x     0     0         0 29-Apr-2010 14:12 PRESEED
-rwxr-xr-x     0     0         0 29-Apr-2010 14:12 UBUNTU
-rwxr-xr-x     0     0   2037229  6-Jan-2010 21:28 usb-creator.exe
-rwxr-xr-x     0     0   1469477 26-Apr-2010 19:06 WUBI.EXE
-rwxr-xr-x     0     0     48565 30-Jul-2010 17:51 Uni-USB-Installer-Copying.txt
-rwxr-xr-x     0     0      4951  2-Sep-2010 04:13 Uni-USB-Installer-Readme.txt

"list of files in the third partition"

http://www.cgsecurity.org
   * FAT12                19203   0  1 19203 254 63      16065
Directory /

drwxr-xr-x     0     0         0 17-Jan-2009 13:40 grub


```

The second partition listed as PENDRIVE is actually my ex D: partition in XP, or at least I think so...I am going to leave my computer with testdisk running until you find out what I should do, hope you can help. And anyway thanks for your advice until now, and sorry for messing up my computer that much...

---

### Post by camoledge on 2010-09-18
Hi. Everyone. i am glad to tell you that my netbook is actually running Ubuntu with no problems. Christophe Grenier after giving me some tips on how to use testdisk told me to try to format my hard drive (I had a backup copy so it was not going to be a problem to lose data) and wipe it clean to then write a new filesystem. Result...I formatted my hard drive in ext2 then decided to try first Jolicloud (awesome idea for an OS in my opinion) and then Ubuntu 10.04. My Netbook has never been so fast and I am also starting to get to understand how to use a terminal. NICE!

---

