---
title: "how to reinstall grub to windows partition"
date: 2011-06-26
forum: General Help
---

### Post by marclane on 2011-06-26
Hi

So, I'm stuck in GRUB rescue mode (stupid mistake) on a dual booted netbook (so no cd and no recovery software)

I do have a Live USB so I'm working off that.

Is there a way to reinstall the GRUB to my other partition (windows 7) or fix the MBR without recovery software?

I know "Google is my friend" but google can be unhelpful sometimes, especially when you're a noob like me.

---

### Post by Rubi1200 on 2011-06-26
If you are currently on the LiveUSB, the best thing to do so we can see what is going on is the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by motsteve on 2011-06-26
As a suggestion also, I would highly recommend using one of your spare usb sticks to store PMagic on it for rescues like this.  It will not only run on its own, but provides many useful utilities for repairing your non booting OS.  In your case the utility to use will be either Super Grub 1 or 2, which are both at the bottom of the boot menu under "extras" of PMagic.  I have a stick like this and it has bailed my butt out countless times.  Of course, I'm always "fixing" my multibooting system all the time since I love to play with all new distros.   :)

Best of luck,

Steve

---

### Post by marclane on 2011-06-26
While I'm doing that: Can I fix this problem by reinstalling the Ubuntu Partition I had accidentally removed and therefore grub with it? If I install it in exactly the same partition, with the same specs?

---

### Post by Rubi1200 on 2011-06-26
That would probably also work. The problem is that even though you removed the Ubuntu partition, traces of GRUB are left in the MBR.

There is also another possible way to fix this, but it is your choice.

---

### Post by marclane on 2011-06-26
Ok so last issue: My hard disk is divided into to partitions, C & D, which I had labeled Local Disk (C) and Media Disk (D). However I can't seem to get to the C drive with the live usb. How can I fix this? I'd like to see if I can save some of the most important files on there

---

### Post by Rubi1200 on 2011-06-26
That is why I suggested posting the results of the boot script; so we can get a better overview of what is going on.

---

### Post by marclane on 2011-06-26
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   mount: unknown filesystem type ''
mount: can't open /etc/mtab for writing: Input/output error

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Mounting failed:   mount: unknown filesystem type ''
mount: can't open /etc/mtab for writing: Input/output error
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: can't open /etc/mtab for writing: Input/output error
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
mount: unknown filesystem type ''

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: can't open /etc/mtab for writing: Input/output error
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 1064864 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 NTFS / exFAT / HPFS
/dev/sda2         209,717,248   226,665,135    16,947,888  1b Hidden W95 FAT32
/dev/sda3         226,666,494   488,351,743   261,685,250   f W95 Extended (LBA)
/dev/sda5         241,176,576   485,320,936   244,144,361   7 NTFS / exFAT / HPFS
/dev/sda6         485,324,800   488,351,743     3,026,944  82 Linux swap / Solaris
/dev/sda7         226,666,496   240,445,439    13,778,944  83 Linux
/dev/sda8         240,447,488   241,168,383       720,896  82 Linux swap / Solaris
/dev/sda4         488,351,744   488,392,064        40,321  ef EFI (FAT-12/16/32)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4238 MB, 4238606336 bytes
78 heads, 13 sectors/track, 8164 cylinders, total 8278528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     8,278,527     8,270,336   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       79b34ed7-b9a1-2e47-806b-d3cf61ddc455   ext2       casper-rw
/dev/sda2        86F4-D40A                              vfat       x‡—š
/dev/sda5        AC04A4BF04A48DC0                       ntfs       Media Disk
/dev/sda6        98c77731-4036-4542-bed9-11078c65b266   swap       
/dev/sda8        4122a632-9328-440f-babd-c470568a9d4b   swap       
/dev/sdb1        5BB4-A519                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/loop1       /cow                     ext2       (rw,noatime,errors=continue)
/dev/loop1       /media/casper-rw         ext2       (rw,nosuid,nodev,relatime,errors=continue)
/dev/sda2        /tmp/BootInfo0/sda2      vfat       (ro,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb1        /casper-rw-backing       vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 8e c0  |.1.......|...W..|
00000010  fb fc bf 00 06 b9 00 01  f3 a5 ea 1f 06 00 00 52  |...............R|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 21 01 4d 69  |.RPf1.f..f..!.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 8d 64 10 66  |..A......{...d.f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 62 00 4d 75 6c  |.......fa..b.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 13 81 3e fe 7d 55  |F.f.D..0.r..>.}U|
00000150  aa 0f 85 06 ff bc fa 7b  5a 5f 07 fa ff e4 e8 1e  |.......{Z_......|
00000160  00 4f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  |.Operating syste|
00000170  6d 20 6c 6f 61 64 20 65  72 72 6f 72 2e 0d 0a 5e  |m load error...^|
00000180  ac b4 0e 8a 3e 62 04 b3  07 cd 10 3c 0a 75 f1 cd  |....>b.....<.u..|
00000190  18 f4 eb fd 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 a8 01 0d 0a  |................|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 10 28 00  |.X.MSWIN4.1...(.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 80 0c  |........?.......|
00000020  b0 9a 02 01 50 20 00 00  00 00 00 00 08 00 00 00  |....P ..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0a d4 f4 86 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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

Unknown BootLoader on sda3

00000000  4c be f0 d1 68 28 6a 06  6c dd 5b 5a fa 22 b8 f5  |L...h(j.l.[Z."..|
00000010  3e ce 0e 79 12 fb 2d 3c  18 ae cc a2 18 17 3b 90  |>..y..-<......;.|
00000020  f4 a5 22 72 4c c1 21 04  7f 56 17 82 8f cd 0b ad  |.."rL.!..V......|
00000030  48 71 72 71 0c 96 7c ca  5e 9c e9 34 67 29 80 69  |Hqrq..|.^..4g).i|
00000040  e7 99 09 f4 21 db c0 62  6f 05 0b 4c c8 5a 90 94  |....!..bo..L.Z..|
00000050  6b b4 0b 02 64 9f 3f 3f  8b ae b5 04 d1 67 d7 3b  |k...d.??.....g.;|
00000060  ba a7 63 70 70 45 52 16  b7 53 86 59 44 16 d7 68  |..cppER..S.YD..h|
00000070  ef 10 ec e3 d8 bd 3a df  84 35 a9 36 d2 c3 71 b7  |......:..5.6..q.|
00000080  6f 14 8b b7 04 82 10 a7  a7 2a 13 c1 d3 26 f6 9f  |o........*...&..|
00000090  37 c2 81 7f b7 ee 7c 65  b7 06 d6 04 c9 64 61 34  |7.....|e.....da4|
000000a0  17 25 c6 21 d3 7d b3 b7  93 e4 ce 10 c4 2a 3b 2c  |.%.!.}.......*;,|
000000b0  86 5c 83 55 41 fc 34 9a  3a 56 b3 c6 66 85 47 12  |.\.UA.4.:V..f.G.|
000000c0  d9 e7 c2 d5 22 3e cb bf  e9 bd 44 8a 4c b0 e8 da  |....">....D.L...|
000000d0  f1 7d ef 01 aa 4b 6f ed  6d 80 95 78 45 ec ab fc  |.}...Ko.m..xE...|
000000e0  2d 40 d3 57 67 8f 50 e3  41 66 cc 64 e8 90 3c f9  |-@.Wg.P.Af.d..<.|
000000f0  b4 b7 e9 8e 9e d5 12 20  ca 36 23 38 7a 1a 93 cc  |....... .6#8z...|
00000100  a5 a7 8d 13 76 fc 57 5e  9b db 0c b1 8d 48 03 cd  |....v.W^.....H..|
00000110  4e aa cd e7 ab 06 d4 c1  17 30 ad 60 af 2f 6f fd  |N........0.`./o.|
00000120  b3 a3 a1 ee bd db a8 49  78 c9 f5 1f bf f3 80 73  |.......Ix......s|
00000130  78 f3 16 77 62 b8 30 ac  b8 af 86 e8 79 d1 b6 d8  |x..wb.0.....y...|
00000140  b7 59 5e 3b 5a 80 e8 f5  21 f4 17 cf 42 e0 b5 7c  |.Y^;Z...!...B..||
00000150  85 fe 20 e1 92 f9 ef d7  b8 7f e9 d1 6a 49 bd 5e  |.. .........jI.^|
00000160  5d b0 94 eb dc 95 de da  c8 11 d2 aa 6d 84 03 e1  |]...........m...|
00000170  f3 d3 7e b9 f7 c4 1c 7e  c7 1b 2e b8 e8 39 3d 04  |..~....~.....9=.|
00000180  0c 0a 97 ef c6 02 6c 08  e4 3d 1d 9d 65 07 f0 84  |......l..=..e...|
00000190  44 84 69 c8 79 f5 7d 67  d4 c1 db 52 85 a6 b3 db  |D.i.y.}g...R....|
000001a0  ad fa d1 48 19 8e 11 24  4d 20 1f 1b c1 03 a6 57  |...H...$M .....W|
000001b0  7e 73 b6 5b b2 d3 d6 f1  38 c3 bb 88 b8 87 00 fe  |~s.[....8.......|
000001c0  ff ff 07 fe ff ff 02 68  dd 00 e9 58 8d 0e 00 fe  |.......h...X....|
000001d0  ff ff 05 fe ff ff 84 cb  6a 0f 7e 34 2e 00 00 00  |........j.~4....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
/home/ubuntu/Desktop/boot_info_script.sh: line 2457: cd: /cdrom
/casper-rw-backing/: No such file or directory

---

### Post by Rubi1200 on 2011-06-26
Thanks for posting the results. 

There are, unfortunately, all kinds of errors going on here and I do not want to offer advice without the comments of some other users.

I will send a message to those users asking them to comment.

In the meantime, please be patient and do nothing (hard I know but important in this situation) and wait until we can figure out a way for you to at least save your data (do you have backups?).

Thanks.

---

### Post by oldfred on 2011-06-26
Did you use testdisk to try to restore old partitions, but somehow mixed up old and new so they are not correct? Win7 in sda5 is unusual unless you had another windows booting from sda1. But the one in sda5 says it starts at 2048 which should be sda1. Or is it a copy.

All the others do not mount. Partition table shows partitions, so maybe they are repairable with chkdsk. Windows type partitions have to have NTFS or FAT signatures in the partition boot sector that match the partition table. 

Just to have a copy of this to restore easily I would do this. You could hand create it from the info in the boot script. Then try chkdsk from windows repair CD which is not easy to create on a USB but can be done. (I used windows repair  CD to install itself to USB). Not sure if there is an offical way.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

---

### Post by motsteve on 2011-06-26
I've found it to be true and have heard it always explained the same way to me, that Windoz only likes to be on the first partition of the first disk.  I don't know why.  That is not the problem here maybe, but it could contribute to the garfing up of the boot.  I noticed also that boot loaders are on more than one partition.  This also may not be a problem, but why they're there is beyond me.  I believe SuperGrub 1 or 2 can repair your mbr or you can use the Windoz repair disk.  Just make sure it corrects the mbr on /dev/sda.

---

### Post by Quackers on 2011-06-26
It appears that sda4 is a EFI partition. This isn't a Mac is it?
I believe that some boot boosters use this type of partition too, although I'm not sure exactly what impact it may have on things.

---

### Post by oldfred on 2011-06-26
I have seen some newer portables with the efi partition. If you are using BIOS mode then the efi may not be used for much. But efi supports the newer UEFI boot and may have some important system settings, so I would leave the efi partition. 

The UEFI boot works with gpt partitions and this has BIOS and MBR(msdos), so I am not sure why some systems have the efi partition, maybe just to get started on the idea??

---

### Post by Quackers on 2011-06-26
oldfred, as I've seen this a few times where the system uses a boot booster, maybe this EFI partition is used by those programs in some way to shorten the boot time?
It's a very grey area for me :-)

---

### Post by oldfred on 2011-06-26
By definition the efi partition is part of the system for UEFI boot, but I assume vendors may not follow standards. 

As I understand this, each vendor has a EFI boot folder in the efi partition. Then under UEFI everyone is supposed to use /efi/boot.

EFI System Partition Subdirectory Registry
[http://www.uefi.org/specs/esp_registry](http://www.uefi.org/specs/esp_registry)

---

### Post by srs5694 on 2011-06-26
> **oldfred said:**
> By definition the efi partition is part of the system for UEFI boot, but I assume vendors may not follow standards. 

Correct. It's often present on GPT disks, since GPT is part of the (U)EFI spec and since Windows will boot *only* from GPT disks on UEFI-based systems. There is, however, an EFI type code for MBR disks. Linux should be able to boot from an MBR disk using UEFI firmware, but I've never tested this myself.

> As I understand this, each vendor has a EFI boot partition. Then under UEFI everyone is supposed to use /efi/boot.

Not quite. Normally each disk on a (U)EFI computer has *one* EFI System Partition (ESP), and each OS vendor has one *subdirectory* in the EFI directory on the computer's boot disk. In Linux, the ESP is usually mounted at /boot/efi, so you'll end up with directories like /boot/efi/EFI/ubuntu, /boot/efi/EFI/redhat, /boot/efi/EFI/Microsoft, and so on.

Given that the OP's disk is an MBR disk that seems to have Windows installed on it, my guess is that the ESP on this disk is unimportant; however, it's conceivable that there's some unusual boot loader software installed on the disk that's using the ESP for some non-standard or almost-standard purpose.

---

### Post by coffeecat on 2011-06-27
I've delayed posting because I have nothing intelligent to say about efi partitions and wanted to see what others had to say about them. I do have a question for m'learned friends, though. The efi partition is tucked right up at the end of the hard drive. I realise that this won't affect its functionality, but isn't that a bit odd? I would have thought that the first partition was a more obvious place for it. Perhaps it's related to what oldfred mentioned, that what is probably the Windows C: partition is a logical one (sda5) but which reports that its start sector is the start sector of sda1. Which would make sense if the Windows boot files were in sda1, but it's still an unusual configuration. I have a few questions of the OP.

@marclane, what make and model netbook is this? When you first installed Ubuntu, did you take a note of the original partition layout? What option did you choose in the partitioning stage of the installer? You have two swap partitions. Do you know why? Have you tried to install Ubuntu more than once? And you haven't answered oldfred's question yet: have you used testdisk at any stage?

I think we also need to consider the mount failure and/or "unknown filesystem" that the boot script reports for every partition except the two swap partitions. Also - blkid fails to see sda1, sda7 and sda4.

---

