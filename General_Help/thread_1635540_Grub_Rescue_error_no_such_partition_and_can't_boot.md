---
title: "Grub Rescue error: no such partition and can't boot to live CD/USB!"
date: 2010-12-01
forum: General Help
---

### Post by ubigT on 2010-12-01
I have a netbook that dual-boots Win XP and Ubuntu 10.04 and accidentally hit the Win recovery mode in GRUB today, but quickly restarted without formatting or proceeding with any recovery.  But upon reboot I just see:
error: no such partition.
grub rescue>

What I have tried so far: Boot to USB Live Disk... It won't, just goes straight to grub rescue.
I do **ls** and it gives me 
(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) (fd0)
error: fd0 cannot get C/H/S values.

**set** gives me 
prefix=(hd0,5)/boot/grub
root=hd0,5

but if I try to **boot** it says unknown command so I figured I needed to find the right partition to boot from but I went through all of them with **ls (hd0,4)/boot**, **ls (hd0,3)/boot** etc. and every partition comes back "unknown filesystem".
So at this point I am stuck.  Any advice would be much appreciated!

---

### Post by oldfred on 2010-12-01
It must have started to install something. Lets see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by ubigT on 2010-12-02
So I was able to boot to USB after making some BIOS changes, here's my boot info:

               ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,057,906   167,057,844   7 HPFS/NTFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4         167,059,454   302,245,887   135,186,434  15 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1002 MB, 1002438656 bytes
31 heads, 62 sectors/track, 1018 cylinders, total 1957888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     1,956,595     1,956,534   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2CFC21C1FC2185E4                       ntfs                                     
/dev/sda2        CCED-990E                              vfat                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B44D-3D4A                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  71 35 18 9c 84 6c 4e 4e  fc e8 6e ad b4 fd 12 0c  |q5...lNN..n.....|
00000010  61 5c 0a dd d9 0c 7d 1d  34 79 77 e2 65 ca 74 31  |a\....}.4yw.e.t1|
00000020  c7 45 23 70 f7 39 ce df  49 1d c4 01 90 02 65 e8  |.E#p.9..I.....e.|
00000030  1e 72 02 3a 09 d5 48 b9  4a 78 1a 7c bd 21 77 b9  |.r.:..H.Jx.|.!w.|
00000040  3d 70 2d f0 28 81 2c bc  ee 54 38 ac 1d d6 16 98  |=p-.(.,..T8.....|
00000050  17 12 84 17 7b 99 8d b4  19 aa ae 56 46 b6 78 22  |....{......VF.x"|
00000060  04 66 08 c9 1b 93 7c 08  21 db cb b2 4c 1b f2 cb  |.f....|.!...L...|
00000070  54 c8 7d ea 27 ea 1a bc  c0 a0 06 90 4f 9d 63 6f  |T.}.'.......O.co|
00000080  64 c8 11 16 ab dd 13 3b  d4 96 89 cd c0 20 2a 81  |d......;..... *.|
00000090  30 2c 44 8b a7 13 c3 a5  a0 e1 a5 dd ab 15 74 b2  |0,D...........t.|
000000a0  8b 67 71 2d a4 ab d5 db  d3 26 36 ab c7 26 0e 84  |.gq-.....&6..&..|
000000b0  a2 c1 86 b5 03 d4 b9 b6  c6 f6 84 89 8d ea ad 8f  |................|
000000c0  47 70 d4 d6 3d cb 57 2c  89 e3 11 4c ee c5 8f 37  |Gp..=.W,...L...7|
000000d0  68 76 5f fb 25 b8 bc 4b  03 d0 80 80 c6 0b 43 0f  |hv_.%..K......C.|
000000e0  d0 e5 2b 9a 92 1d 55 f7  f1 38 80 b3 57 e7 66 72  |..+...U..8..W.fr|
000000f0  5f 9e c0 8c 6d 18 38 d5  19 c8 a8 3d 22 39 37 14  |_...m.8....="97.|
00000100  5a a6 7a 2d 01 c7 cc 99  33 50 dc f3 25 8c 26 71  |Z.z-....3P..%.&q|
00000110  58 83 dc a6 9b fe f1 7c  ea 42 07 54 d5 cb 6d b8  |X......|.B.T..m.|
00000120  66 63 00 a5 fc ce c5 6a  d8 d5 70 ee 95 15 cb a5  |fc.....j..p.....|
00000130  be 65 0b ec c1 7d 62 ed  16 c1 30 13 12 6b f1 f9  |.e...}b...0..k..|
00000140  d6 dd 28 ae e3 af e2 69  a8 4e 41 b2 a8 80 33 d8  |..(....i.NA...3.|
00000150  25 55 ca e7 2f ae 5a 05  43 6e 95 2f 58 56 26 d7  |%U../.Z.Cn./XV&.|
00000160  0f 4e 87 53 ef 41 71 9b  a5 b6 61 b5 43 3e f9 d8  |.N.S.Aq...a.C>..|
00000170  4c 25 49 c1 47 90 c5 f2  85 84 f2 cf 8b 36 b4 55  |L%I.G........6.U|
00000180  7f d1 50 7d b1 7a 49 60  a0 b8 ad d0 22 9f bc a5  |..P}.zI`...."...|
00000190  f1 a4 bd ff 1e b9 31 21  f4 b1 7c c1 56 be 7b 43  |......1!..|.V.{C|
000001a0  6b f5 3f 4f 56 5f 68 08  6c e5 f9 23 29 1f be 27  |k.?OV_h.l..#)..'|
000001b0  98 5f ac 46 0d 5b e8 25  c2 d8 a8 db 4f e8 00 fe  |._.F.[.%....O...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 b9 07 00 fe  |...........H....|
000001d0  ff ff 05 fe ff ff 02 48  b9 07 00 80 55 00 00 00  |.......H....U...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2010-12-02
It looks like it already rewrote partition table as you have sda3 & sda4 that are not standard. Do you have an efi type boot instead of BIOS or one that lets you choose. It looks like the recovery rewrote a efi partition.

You might try testdisk.
enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Or you may just have to reinstall.

---

