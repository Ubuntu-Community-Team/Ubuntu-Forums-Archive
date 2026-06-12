---
title: "wubi update to 10.10 stuck at grub rescue and cant locate impotant data"
date: 2011-01-05
forum: General Help
---

### Post by kellym on 2011-01-05
So here's my story...
Dell Inspiron E1405 - 160 GB drive with 2 partitions - I think only 1 partition was used for windows and ubuntu
Used wubi to install 10.04 - both XPP and 10.04 worked fine after repairing the XP install
My  boyfriend used Referencer (.reflib) in Ubuntu 10.04 to organize and tag  about 900 documents.  He spent around 9 hours on the project and its  VERY IMPORTANT.
I am a dumb ***, forgot the project was on the computer and updated to 10.10 via update manager without it backing up.  ](*,)
Now I cant boot to XPP or Ubuntu -  "error: no such device:", "grub rescue"
My main concern is getting the data back.  I  would rather uninstall WUBI and install Ubuntu on the 2nd partition (wish I would have done this in the first place but 10.04 was my first Ubuntu install and I didn't know any better).  
I have to get this data back!
I have tried the following and cant locate the referencer (.reflib) file or the .docs and .jpgs

[LIST]
[*] booted to USB using my 10.10 netbook remix USB install USB stick - I can see the windows files
[*]pulled the HD out and connected it to my Ubuntu netbook, an XPH and W7 computers -cant locate data
[/LIST]

Questions:
Did the update erase my data?
If it did, how do I get it back?
If it didn't, where is it?


Here's the Boot Info
Someone please help me!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: ************************************************************************_

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: ************************************************************************_

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: ************************************************************************_

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: ************************************************************************_

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ******************_ ************************************_________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   112,647,779   112,647,717   7 HPFS/NTFS
/dev/sda2         112,647,780   234,436,544   121,788,765   7 HPFS/NTFS


Drive: sdb ******************_ ************************************_________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
5 heads, 32 sectors/track, 48921 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   b W95 FAT32


blkid -c /dev/null: ******************************************************______

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       9d4df811-5484-4196-84f5-fe320301092b   ext4                                     
/dev/sda1        72DC9D83DC9D4271                       ntfs                                     
/dev/sda2        8A64E1EC64E1DAC9                       ntfs       Ubuntu                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DA03-353B                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr="Ubuntu"  
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 50 77 00 c6 1d 00 00  00 00 00 00 02 00 00 00  |.Pw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 3b 35 03 da 4e  4f 20 4e 41 4d 45 20 20  |..);5..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 78 f9 15 00  66 ba 00 00 00 00 bb 00  |}.f.x...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by anystupidname1 on 2011-01-05
Questions:
Did the update erase my data? **No.**
If it did, how do I get it back? **There are ways to recovery data but I wouldn't recommend getting into that until you've made sure it is gone...**
If it didn't, where is it? **If you know the names of the files, once you've booted from a liveCD and mounted all partitions, you can try searching for the file(s) with a command like this:**
```
sudo find / -name filename
```

---

### Post by wilee-nilee on 2011-01-05
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

You will need the MS bootloader in the MBR or the Linux one that works. Grub doesn't work under in a wubi environment. Do you ahve a XP cd, if not that is okay we can boot a live Ubuntu cd/thumb and use lilo

Can't gaurantee anything about wubi though at this point.
sda2/Wubi: ************************************************************************_

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

It just may need a fix, but wubi is not designed for the way you used it.
#1 upgrading. 
#2 relying on it to be a place important work is kept that is not backed up.
#3 long term use overall. 
Wubi is okay but using it for more then trying out Ubuntu for a actual dual boot is okay but have that stuff backed up some where else.

It may be that if we get back into XP that you will at the least get to the wubi files, maybe even boot in hard to say.

---

### Post by bcbc on 2011-01-05
As Wilee Nilee says, just reinstall the windows bootloader or use lilo. This is a very common problem and usually there is no other issue after replacing the bootloader:
Sometimes bootinfoscript can't read the wubi root.disk but it doesn't always indicate a problem.

See the [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #1, Solution #1 or #2 for reinstalling the windows bootloader.

Then boot windows and ubuntu - and report back if you have any problems.

PS if you reinstall the windows bootloader using an XP disk you just need the "fixmbr" command, not the "fixboot" command.

---

### Post by anystupidname1 on 2011-01-05
Good point. Mounting the wubi image wouldn't happen automatically. If your files are in there, make sure you mount that image and check in there.

sudo mount -o loop /media/<wherever that WUBI image is>/ubuntu/disks/root.disk /media/whatever

---

### Post by wilee-nilee on 2011-01-05
> **bcbc said:**
> As Wilee Nilee says, just reinstall the windows bootloader or use lilo. This is a very common problem and usually there is no other issue after replacing the bootloader:
Sometimes bootinfoscript can't read the wubi root.disk but it doesn't always indicate a problem.

See the [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #1, Solution #1 or #2 for reinstalling the windows bootloader.

Then boot windows and ubuntu - and report back if you have any problems.

PS if you reinstall the windows bootloader using an XP disk you just need the "fixmbr" command, not the "fixboot" command.

When I see a wubi problem I immediate wonder where you or Rubi1200 are, thanks for posting.:)

---

### Post by bcbc on 2011-01-05
> **wilee-nilee said:**
> When I see a wubi problem I immediate wonder where you or Rubi1200 are, thanks for posting.:)

I can't help it :) Lately with Wubi and Grub it's like a train wreck and I can't pull myself away - lol

---

