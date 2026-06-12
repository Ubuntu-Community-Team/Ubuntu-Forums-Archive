---
title: "Grub Error No Such Partition"
date: 2011-09-25
forum: General Help
---

### Post by elfed up on 2011-09-25
Please Help Me!!!! 
So, I had Xp installed and I installed Ubuntu along side it and everything was great! I then realized I dont need Ubuntu on this computer any more so I deleted its partition using windows disk manager. Aparently the bootloader was on the Ubuntu partition so I now Can't boot windows!!! I am on the LiveCD now so I can use terminal but I cant get onto the windows Recov. console. I used the bootinfo and my results are: 
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   151,920,962   151,920,900   7 NTFS / exFAT / HPFS
/dev/sda2         151,922,686   195,371,007    43,448,322   5 Extended
Extended partition linking to another extended partition.
/dev/sda5     ? 3,597,154,926 4,267,447,120   670,292,195   2 XENIX root

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        86007AC884924782                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ef 5b 26 e8 4b 18 a9 53  22 58 4b 75 8e 3e 31 cd  |.[&.K..S"XKu.>1.|
00000010  ce c0 95 2e 01 49 2f 07  f7 80 31 b9 58 70 69 75  |.....I/...1.Xpiu|
00000020  2e 88 08 f3 0e 2b 0e e3  64 96 fa cd f3 1b 2c e4  |.....+..d.....,.|
00000030  09 cb fc 06 da c9 6a 96  c5 b1 10 ac 9a 40 58 89  |......j......@X.|
00000040  9d df 93 63 9c c1 c1 81  16 a3 f6 7f 7f 26 a5 72  |...c.........&.r|
00000050  80 81 72 f6 2b b5 9b 73  18 0c 92 94 16 9c 92 fa  |..r.+..s........|
00000060  ad 95 78 4f f9 aa 6e d2  87 92 5d 7a 1f 3c c9 6b  |..xO..n...]z.<.k|
00000070  da 0a cd 0f 29 7e 9f e9  0f af 4a 41 09 26 24 fb  |....)~....JA.&$.|
00000080  47 1d 1c e3 96 76 ac 01  88 86 75 ad 0b a4 c7 78  |G....v....u....x|
00000090  03 3f 26 ee c5 09 2f fa  56 db 12 ce e7 84 0c 7e  |.?&.../.V......~|
000000a0  76 4a 2d b9 50 45 29 d3  ad db fb 87 f4 fa cc 1a  |vJ-.PE).........|
000000b0  4a 36 3a 0c 97 4d d9 f1  ad f5 c5 cf d3 c2 98 56  |J6:..M.........V|
000000c0  a3 8f 2d 2c 7e c8 4e b3  04 2f 3f ad 7b 25 ab 5e  |..-,~.N../?.{%.^|
000000d0  b3 4e f2 3c 9f aa 36 94  86 11 97 1b 3a 5d f0 a6  |.N.<..6.....:]..|
000000e0  13 73 b3 56 57 01 4d 89  90 c1 ef 86 3b bd 64 56  |.s.VW.M.....;.dV|
000000f0  2c 50 3b 72 26 6b fc 55  52 6a 8a d1 37 3b 8f 9a  |,P;r&k.URj..7;..|
00000100  34 3f 4a 86 7d 0d 2d d6  9e ef 23 38 f4 a3 2b 68  |4?J.}.-...#8..+h|
00000110  ab f1 2d c1 ff 9e f1 21  4d 95 20 41 f9 22 97 f7  |..-....!M. A."..|
00000120  21 cd b0 8d f5 47 ae e5  8b 2d f7 c1 c2 cf 32 68  |!....G...-....2h|
00000130  c3 15 11 7d e9 b9 72 c2  a2 91 6d ae e4 b4 98 f4  |...}..r...m.....|
00000140  a3 cd ec ee 90 25 b7 5f  cd a9 f5 44 87 dd 64 a7  |.....%._...D..d.|
00000150  97 ba 6c 44 ca 52 31 d2  75 86 c5 42 b9 24 6d 6c  |..lD.R1.u..B.$ml|
00000160  b0 6c 37 d4 e6 12 f1 67  24 4d 96 66 d1 3c d0 e6  |.l7....g$M.f.<..|
00000170  ad e0 35 e2 c2 83 bb 93  48 1e ea fa 33 95 81 9b  |..5.....H...3...|
00000180  98 b9 e2 ee f5 ba 76 26  27 a1 8f 78 ef d5 13 23  |......v&'..x...#|
00000190  47 14 aa d8 cb 94 77 45  a4 8f 50 37 50 66 11 9f  |G.....wE..P7Pf..|
000001a0  03 34 a2 69 e9 64 01 cf  08 cd 12 fb 51 d3 30 01  |.4.i.d......Q.0.|
000001b0  52 1e 12 28 1c a9 29 b7  a9 06 bd 42 38 4f 00 fe  |R..(..)....B8O..|
000001c0  ff ff 05 fe ff ff c3 0f  57 02 3f e8 3f 00 00 00  |........W.?.?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5



=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory

```

---

### Post by garvinrick4 on 2011-09-25
Use your Xp disk and replace windows boot manager. Instructions below.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
If do not have a windows disk use Live cd from Ubuntu (install cd and use Try Ubuntu)
Open a terminal (ctrl/alt/t and copy and paste two commands.
Restore basic windows boot loader - universe enabled 
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR
Now reboot into windows

Should use disk manager or gparted in Live cd and straighten up your partition table.
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by ajgreeny on 2011-09-25
It looks to me as though you installed ubuntu inside Windows using wubi, and then installed grub to the MBR which was not correct.

Am I right?  If so you will need to restore the windows MBR which you can do from a live ubuntu CD with lilo ```
sudo apt-get install lilo
``` Ignore the warning then ```
sudo lilo -M  /dev/sda mbr
```Then you should be able to boot directly into Windows again if all goes well.

Ignore this if you did partition and install that way, though there is no sign of ubuntu partitions in your boot-info-script output.  After doing this you may not have the option to boot to ubuntu as the windows bootloader files will not know that ubuntu is even installed, so you may need to uninstall ubuntu from windows and then install it again.

EDIT:
Sorry but I didn't notice you had removed ubuntu and I missed garvinrick4's post which I have repeated partly.

---

