---
title: "Problems with Boot"
date: 2010-02-22
forum: General Help
---

### Post by andrezp on 2010-02-22
Hi, I'm having problems with Grub for Boot in XP and W7.

**_First of All:_** I have searched, and I found no solutions that worked for me, I have also checked outside sources, and used a W7 repair disk to attempt to repair the boot for Windows, also used XP repair disk.

When I try to boot XP:
            Error 12: Invalid Device requested.

The configuration of Grub 
> 
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 272897870 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, 312581808 sectores en total
Units = sectores of 1 * 512 = 512 bytes
Disk identifier: 0x3fa33fa3

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   291,611,879   291,595,815   f W95 Ext d (LBA)
/dev/sda5              16,128   112,663,844   112,647,717   7 HPFS/NTFS
/dev/sda6         112,663,908   267,048,494   154,384,587   b W95 FAT32
/dev/sda7         267,048,558   288,013,319    20,964,762  83 Linux
/dev/sda8         288,013,383   291,611,879     3,598,497  82 Linux swap / Solaris
/dev/sda2    *    291,612,672   291,817,471       204,800   7 HPFS/NTFS
/dev/sda3         291,817,472   312,578,047    20,760,576   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, 312581808 sectores en total
Units = sectores of 1 * 512 = 512 bytes
Disk identifier: 0x3fa23fa2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   302,070,194   302,070,132   c W95 FAT32 (LBA)
/dev/sdb2         302,070,195   312,560,639    10,490,445   f W95 Ext d (LBA)
/dev/sdb5         302,070,258   312,560,639    10,490,382   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        EC38DE2F38DDF892                       ntfs       Reservado para el sistema     
/dev/sda3        B64C27BA4C277471                       ntfs                                     
/dev/sda5        66E8B867E8B836E1                       ntfs       XP                            
/dev/sda6        031A-031B                              vfat       DATOS2                        
/dev/sda7        ed98646a-597d-48f9-abb2-5b065452e642   ext3                                     
/dev/sda8        0471ac17-0a07-4f18-b898-84686daac715   swap                                     
/dev/sdb1        06F8-06FB                              vfat       DATOS                         
/dev/sdb5        BC4C8C674C8C1DF0                       ntfs       NTFS                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,acl,user_xattr)
/dev/sda3        /mnt/W7                  fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /mnt/W7Boot              fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /mnt/XP                  fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /mnt/datos               vfat       (rw,noexec,nosuid,nodev,gid=100,umask=0002,utf8=true)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== sda7/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on dom feb 21 21:16:03 ARST 2010
default 2
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,6)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title SUSE LINUX 
    root (hd0,6)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part7    repair=1 resume=/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part8 splash=silent showopts vga=0x317
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- SUSE LINUX 
    root (hd0,6)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part7 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd

title Windows XP
    rootnoverify (hd0,4)
    makeactive
    chainloader +1

title Windows 7
    rootnoverify (hd0,1)
    makeactive
    chainloader +1

title sda1
    rootnoverify (hd0,0)
    chainloader +1

title sda3
    rootnoverify (hd0,2)
    chainloader +1

=============================== sda7/etc/fstab: ===============================

/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part8 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part7 /                    ext3       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part3 /mnt/W7              ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=es_ES.UTF-8 0 0
/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part2 /mnt/W7Boot          ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=es_ES.UTF-8 0 0
/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part5 /mnt/XP              ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=es_ES.UTF-8 0 0
/dev/disk/by-id/ata-SAMSUNG_HD161HJ_S0V3J1GP401001-part6 /mnt/datos           vfat       users,gid=users,umask=0002,utf8=true 0 0

=================== sda7: Location of files loaded by Grub: ===================


 139.7GB: boot/grub/menu.lst
 139.7GB: boot/grub/stage2
 139.7GB: boot/initrd
 139.7GB: boot/initrd-2.6.27.7-9-default
 139.7GB: boot/vmlinuz
 139.7GB: boot/vmlinuz-2.6.27.7-9-default
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 20 20 00  |.X.PARAGON#..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  cb b8 33 09 2a 93 00 00  00 00 00 00 02 00 00 00  |..3.*...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1b 03 1a 03 4a  20 20 20 20 20 20 20 20  |..)....J        |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda8

00000000  71 1c 24 0b 82 80 44 12  18 9c a9 ee 1f 55 70 0d  |q.$...D......Up.|
00000010  31 3e aa 7e af dd 1e 15  fe 83 10 01 4c d2 68 65  |1>.~........L.he|
00000020  1f 79 5d e9 7d 45 27 54  4b c8 3e 88 df f5 7f 6f  |.y].}E'TK.>....o|
00000030  c9 cf 89 20 a0 bf 1f f9  56 41 ef a7 ae 67 15 7b  |... ....VA...g.{|
00000040  d3 6d 44 5a f6 74 c8 b9  c4 6e 6c e7 24 56 bf df  |.mDZ.t...nl.$V..|
00000050  8b 2e fb 56 61 50 c4 8f  ee ce a2 5a 8c d9 cd 5b  |...VaP.....Z...[|
00000060  5f 64 d9 ea f0 29 d0 70  5a c3 82 dc 16 5f 4e bc  |_d...).pZ...._N.|
00000070  83 ed 79 ef 70 53 e5 9b  52 3f 4e 4b c9 51 3d 9d  |..y.pS..R?NK.Q=.|
00000080  81 23 dc c3 0e 26 45 37  bc 33 44 87 4f d7 bd 80  |.#...&E7.3D.O...|
00000090  5c 7f be 38 a0 1c 04 e3  9e 18 e9 b7 28 61 37 4b  |\..8........(a7K|
000000a0  fc 0c 6f 37 e9 0e 01 67  8f 27 12 b7 5b d7 bc 33  |..o7...g.'..[..3|
000000b0  4c c4 19 fe 13 bf 3f d8  e0 2c 82 32 2d 20 cf 67  |L.....?..,.2- .g|
000000c0  65 69 ee 3c 05 30 e1 a0  c6 16 b7 d4 79 95 98 d7  |ei.<.0......y...|
000000d0  73 7a ff 04 10 0f 05 08  95 6a af ef 67 13 5b 8f  |sz.......j..g.[.|
000000e0  b3 d0 7f 27 25 b2 a0 a4  f0 1b be 9f 1e d9 7b 45  |...'%.........{E|
000000f0  1c c3 ae 04 30 ec 3c c3  72 56 e6 ec 7a 8a 81 d4  |....0.<.rV..z...|
00000100  7f 30 10 d5 aa ec b4 6e  e0 6c fc d9 58 79 29 18  |.0.....n.l..Xy).|
00000110  69 00 a9 a0 3c 64 ba 09  1a 24 db 8d 9d 54 23 2b  |i...<d...$...T#+|
00000120  c6 3f a8 be ef 7b 21 79  00 20 c9 1c ae 3e 00 e8  |.?...{!y. ...>..|
00000130  08 5e 9f 8d bf 27 1d a6  8f a5 7e e9 ca 61 ce af  |.^...'....~..a..|
00000140  6d 1f b8 4a 32 2f a2 b1  2e 13 77 4e dc e2 31 8b  |m..J2/....wN..1.|
00000150  85 79 f7 28 20 6f bd ec  08 21 e9 77 d3 ef 70 48  |.y.( o...!.w..pH|
00000160  0a 30 04 82 24 78 c2 fe  72 b9 c8 6e e7 89 a9 cf  |.0..$x..r..n....|
00000170  56 a9 ea 7d 47 a7 1e 18  80 d3 fd fe 94 08 77 1d  |V..}G.........w.|
00000180  ee 08 5e 97 e5 ea 8b a5  d0 86 3f fa 9b 6a df fe  |..^.......?..j..|
00000190  54 5e 97 12 47 fb f7 9f  8b 78 f8 06 80 60 95 82  |T^..G....x...`..|
000001a0  51 78 20 f9 44 57 4b a1  72 ad ea b9 6c b3 3c 9e  |Qx .DWK.r...l.<.|
000001b0  5b 7e f7 08 ca 01 e2 4d  8a be 0a 09 d0 87 3a 10  |[~.....M......:.|
000001c0  cb d8 9f 57 db e4 ef f3  52 e1 9a dd ff fd d8 a4  |...W....R.......|
000001d0  0e fc 0b b3 d6 5f 17 84  b0 c2 66 7f 17 d6 3e eb  |....._....f...>.|
000001e0  19 7f 35 50 ff 62 44 b0  ea 66 56 ef f4 b1 ec c4  |..5P.bD..fV.....|
000001f0  da 71 5f ba a5 9c 76 01  a8 e0 28 bb 57 fd 35 c1  |.q_...v...(.W.5.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 50 41 52 41 47  4f 4e 23 00 02 20 38 00  |.X.PARAGON#.. 8.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  74 39 01 12 f0 1f 01 00  00 00 00 00 dc 08 00 00  |t9..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 fb 06 f8 06 20  20 20 20 20 20 20 20 20  |..)....         |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
If anyone can help me, I'd appreciate any help!

Thank you,
Andres

P.S : Sorry for my poor English...

---

### Post by mörgæs on 2010-02-23
Windows is not playing nicely with other operative systems:
[http://ubuntuforums.org/showthread.php?t=807047](http://ubuntuforums.org/showthread.php?t=807047)

---

### Post by andrezp on 2010-02-23
> **mörgæs said:**
> Windows is not playing nicely with other operative systems:
[http://ubuntuforums.org/showthread.php?t=807047](http://ubuntuforums.org/showthread.php?t=807047)

Thank you for you help.

The problem was a bad entry en boot.ini

---

