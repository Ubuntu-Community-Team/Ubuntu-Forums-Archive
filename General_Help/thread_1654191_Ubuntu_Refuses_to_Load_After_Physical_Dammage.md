---
title: "Ubuntu Refuses to Load After Physical Dammage"
date: 2010-12-28
forum: General Help
---

### Post by ChicosAStar on 2010-12-28
I was in Ubuntu when I dropped my laptop, which resulted in a cracked screen. I loaded Windows (Vista), and found it and the files to be unharmed. On my attempt to load Ubuntu, it takes me to a GRUB screen, where it gives me a default message about GRUB. If I try the command "exit" it replies "No bootable device -- insert boot disk and press any key. It's installed on the same hard drive as Windows (dual boot setup), and Windows works fine. I do have files I would like to get off of Ubuntu (if it is unrecoverable), so simply reinstalling would not help.

---

### Post by Rubi1200 on 2010-12-28
Hi,
do you have a LiveCD?

If yes, boot the computer with it, choosing to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

---

### Post by tgalati4 on 2010-12-28
Chances are good that the hard drive is damaged on the Ubuntu partition.  Since Windows boots, quickly recover files on the Windows partition.  I presume that you are using an external monitor since the screen is cracked.

Then take an Ubuntu LiveCD and boot from it.  Try to mount the Ubuntu partition and see if you can move around.  If so, recover files to a thumb drive.  If you can't mount the disk, then you will have to install testdisk and attempt to do a low-level scan and recovery.  You would need an external USB drive to receive the files.

An alternative method:

Find a desktop machine with Ubuntu and install testdisk.

sudo apt-get install testdisk
man photorec

Purchase an notebook-drive-to-desktop-drive ribbon cable adapter.  Or purchase a notebook drive USB enclosure.  Remove the damaged drive and connect to the desktop computer or put inside the USB enclosure.

Use photorec to scan and recover files to a recovery directory on the desktop machine.

This is an involved procedure that requires time, expense, and patience.

---

### Post by ChicosAStar on 2010-12-28
I actually used the Windows installer to do those, and don't have a CD on hand at the moment. I have already updated my backup of my documents, in case it decides to give in. My Ubuntu install is recent, and is just a few files I was testing out. I appreciate the method, but I think it's quite too much for a few image/video/document files.

---

### Post by ChicosAStar on 2010-12-28
I apologise if there is a rule against double posting, I did not see one. Here are the results to the script you have asked for.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *             63   291,899,391   291,899,329   7 HPFS/NTFS
/dev/sda2         291,899,392   312,573,951    20,674,560   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        709D159D5CA66DB7                       ntfs                                     
/dev/sda2        D03EF07C3EF05CC2                       ntfs       PRESARIO_RP                   
/dev/sda: PTTYPE="dos" 
/dev/sdc1        0804-1466                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/RCT3              iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda2        /media/PRESARIO_RP       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi


Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 50 77 00 c6 1d 00 00  00 00 00 00 02 00 00 00  |.Pw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 66 14 04 08 4e  4f 20 4e 41 4d 45 20 20  |..)f...NO NAME  |
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
00000100  7d 00 66 b8 b4 3b 00 00  66 ba 00 00 00 00 bb 00  |}.f..;..f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Rubi1200 on 2010-12-28
Thanks for the results.

Two things you can try:

1. to rescue any data from the Wubi install;
you can recover your data from the Wubi install from _within_ Windows. In this case, you can use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk. 

2. Run a file-system check from the LiveCD to try and restore the option to boot normally (only do this after recovering data because it may not work);
```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```If this works, try rebooting and see if you can access it normally.

---

### Post by ChicosAStar on 2010-12-28
I tried the ext2explore, and it did not work. I opened it, and had it scan the system. It appeared blank. I did run it as an admin, so I'm not sure what's wrong. Any ideas?

>I did not partion my disk when I installed ubuntu, I just ran the installer. Perhaps that has some cause?

---

### Post by Rubi1200 on 2010-12-28
Did you try running the file-system check I posted about?

What were the results, if any?

---

