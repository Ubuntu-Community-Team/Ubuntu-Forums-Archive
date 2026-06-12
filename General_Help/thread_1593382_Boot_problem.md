---
title: "Boot problem"
date: 2010-10-11
forum: General Help
---

### Post by stab on 2010-10-11
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812   c W95 FAT32 (LBA)
/dev/sda2          20,482,875   239,478,049   218,995,175   7 HPFS/NTFS
/dev/sda3         239,478,782   625,137,344   385,658,563   f W95 Ext d (LBA)
/dev/sda5         333,043,578   625,137,344   292,093,767   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        F0E281A7E2817320                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        F7A601C990830264                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/VistaOS           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  9f 9e 63 aa f9 19 53 87  ff ca 90 09 39 7a 71 16  |..c...S.....9zq.|
00000010  ae e7 59 f8 e8 26 1e fe  d5 a3 bc f5 9c c4 5b 0f  |..Y..&........[.|
00000020  05 39 7f e2 2a 43 bb 3e  66 e1 87 92 8c 3f 97 67  |.9..*C.>f....?.g|
00000030  53 d7 03 9c 7f 6b 17 df  61 1f e4 ea 43 77 f1 d6  |S....k..a...Cw..|
00000040  d0 97 78 eb 27 88 a3 ef  54 58 f8 11 97 0d 05 36  |..x.'...TX.....6|
00000050  72 f4 ee 2e 1e 7e 74 3f  df d1 be 85 a3 d8 83 5c  |r....~t?.......\|
00000060  fd f1 03 1c bd b4 85 4f  4d 28 1c 75 6c e5 fc 83  |.......OM(.ul...|
00000070  87 b9 8a 9f e7 3b f6 44  79 eb d1 07 f9 d0 ca 37  |.....;.Dy......7|
00000080  b9 ba 6b 27 47 af 3e c0  87 5e 79 80 87 a5 6f f3  |..k'G.>..^y...o.|
00000090  d6 e7 5f e2 e1 b5 1e 8e  ce ec e0 ea 3d df e3 53  |.._.........=..S|
000000a0  ef 3c ce 87 96 be cb c3  e8 61 3e 15 f8 3e 47 cf  |.<.......a>..>G.|
000000b0  1c e2 e1 87 4e 70 f5 c8  20 7f 76 cf 9e 7d 3f 92  |....Np.. .v..}?.|
000000c0  10 ea ea ea 5a fb e2 fa  42 83 ff a7 07 9e 7a 62  |....Z...B.....zb|
000000d0  cf be f3 18 a1 e9 46 e4  c6 2a 99 47 64 69 91 a0  |......F..*.Gdi..|
000000e0  19 12 ac 45 ee 70 3a 36  d9 47 50 35 32 b3 14 69  |...E.p:6.GP52..i|
000000f0  48 eb 3f 2d f8 3f 6d f0  22 db ae 76 dc 6b b7 cf  |H.?-.?m."..v.k..|
00000100  cc 47 1a 88 cc c9 64 61  8d ac cc 13 f9 06 d9 58  |.G....da.......X|
00000110  8f 6c bb 72 e4 3e fb b5  c6 2a 99 55 c8 bc 4c 96  |.l.r.>...*.U..L.|
00000120  56 08 9a 27 ca 2c d9 38  1d d9 e6 76 34 96 c8 82  |V..'.,.8...v4...|
00000130  44 16 15 b2 84 c9 ea 32  41 37 89 3c 4b 9a 66 22  |D......2A7.<K.f"|
00000140  5b af 74 dc 44 64 39 40  56 14 b2 8a 08 5a 22 08  |[.t.Dd9@V....Z".|
00000150  62 35 88 3c 13 59 40 64  25 40 56 e1 2d 91 b5 55  |b5.<.Y@d%@V.-..U|
00000160  b2 b6 48 56 e7 c8 ca 0d  b2 ea 46 60 fd 5a 88 ac  |..HV......F`.Z..|
00000170  c9 64 0d 91 b5 65 b2 32  47 16 6f 90 85 99 c8 92  |.d...e.2G.o.....|
00000180  42 96 43 fe 6e cb 12 59  01 6e 0b 64 e9 06 99 9f  |B.C.n..Y.n.d....|
00000190  89 34 6a 9d 8b 41 72 33  44 16 81 18 26 4b cb 64  |.4j..Ar3D...&K.d|
000001a0  a9 41 16 a6 23 8d 6b 9d  10 bd 11 22 b3 41 9f 33  |.A..#.k....".A.3|
000001b0  a4 b3 30 ef af 9f bd d6  39 53 e9 68 60 32 00 fe  |..0.....9S.h`2..|
000001c0  ff ff 07 fe ff ff 7c af  93 05 47 ff 68 11 00 00  |......|...G.h...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
what must ido to repair it it just open grub rescue>  command page when i start laptop

---

### Post by Quackers on 2010-10-11
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

There is no partition #6 - where has it gone? Did you have one? This is why the system won't boot.
Second problem: you don't appear to have a Linux system. No boot files, no partitions, nothing. Were these in sda6 at one time?
More details are needed. Can you tell us what system you had and what you were trying to do before the problem arose?

---

### Post by stab on 2010-10-11
my battert is low and going to go off so i have installed same drive on c: on vista without wubi but it make new partion on c: as sda to install ubuntu i have a recovery hardisk on on laptop not visible about 20 gb i think hd0,6 is that but it install it on hd0,5 but not seen i will use recovery dvd and reinstall ubuntu but if there is a way to repair it it will be better

---

### Post by Quackers on 2010-10-11
Sorry I don't understand that :-(
If you plug your recovery disk in does the system boot up normally?

---

### Post by stab on 2010-10-11
yes i have asus recovery cd for recover vista with full drivers but it will format c: completely but i install ubuntu on c:  with new partition but on windows its not visible it will try to format on this partition i afraid to get  an eror because of it

---

### Post by Quackers on 2010-10-11
Ah, you have a recovery disc (not a backup disc) ok.
According to the boot script you've posted you don't have Ubuntu installed, but you do have grub2.
Something is wrong there.

---

### Post by giddensdb on 2010-10-11
I had Ubuntu and Win Vista installed on my laptop and wanted to replace Win (which I noticed I NEVER used) with another distro and picked Slackware.  I boo-booed and let it put LILO over GRUB.  How do I fix this??  I have a bootable USB with Ubuntu that I can use to make the repairs,:popcorn:

---

### Post by oldfred on 2010-10-11
You can use windows to repair the MBR to boot windows:

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub

You can use the Ubuntu liveCD to install a windows like boot loader lilo that will boot your windows.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Or you can install Ubuntu (not wubi) and it will install a new copy of grub into the MBR that will boot both the new install and your existing windows.

---

### Post by giddensdb on 2010-10-11
No, no... I want to get BACK to GRUB so I can get into Ubuntu.  I installed Slackware over my Win partition.  Right now I boot to lilo and it only has the option for Slackware.  I want to have GRUB with options to Ubuntu as well as slackware.

---

### Post by giddensdb on 2010-10-11
I would just re-install Ubuntu but I didn't make separate areas for /home and /usr so I would lose all my installed programs and such.

---

### Post by Quackers on 2010-10-11
Have a look at this page
[http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

---

### Post by oldfred on 2010-10-11
The problem is you are showing no Linux partitions. No errors are shown so I doubt test disk will find anything, but you may want to try it from the liveCD.

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

---

