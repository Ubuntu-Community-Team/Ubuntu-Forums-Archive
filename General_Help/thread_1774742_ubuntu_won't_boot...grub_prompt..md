---
title: "ubuntu won't boot...grub prompt."
date: 2011-06-03
forum: General Help
---

### Post by MadTeaParticipant on 2011-06-03
I tried turning on my computer yesterday and got a grub rescue> prompt. I ended up booting from a CD, and reinstalling GRUB 2. Installation was complete and so I tried to restart the computer, but still ubuntu wouldnt boot, this time I have a grub> prompt instead of a grub rescue>. 

I'm trying to follow these commands:

[B]set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot[/B]

I get as far as the second command (linux /vmlinuz root=/dev/sda1 ro) and am given an error that says cannot find file or no such filesystem, or somthing like that. I dont know why...ubuntu was installed in the sda1 partition.

I dont really speak this kind of language, but would like to get my computer running again. any help?

---

### Post by mikewhatever on 2011-06-03
Please follow the howto for reinstalling Grub2:
[https://help.ubuntu.com/community/Grub2#SIMPLEST%20-%20Use%20Boot-Repair%20graphical%20tool](https://help.ubuntu.com/community/Grub2#SIMPLEST%20-%20Use%20Boot-Repair%20graphical%20tool)

The commands you posted are for Grub1.

---

### Post by Quackers on 2011-06-03
Did you run any updates before you shutdown last time you used it?

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by MadTeaParticipant on 2011-06-03
```
     Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *    307,337,216   312,578,047     5,240,832   c W95 FAT32 (LBA)
/dev/sda2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sda5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris

/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda5

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6E7A-02EA                              vfat       MEDIADIRECT
/dev/sda5        9300e967-3636-40ee-8b68-964716ae47fd   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/MEDIADIRECT       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 22 18  |.X.MSDOS5.0...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 98 51 12  |........?.....Q.|
00000020  00 f8 4f 00 ef 13 00 00  00 00 00 00 02 00 00 00  |..O.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 ea 02 7a 6e 44  65 6c 6c 4d 44 33 70 6c  |..)..znDellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
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

Unknown BootLoader on sda2

00000000  80 6e 74 79 a0 aa 1a 81  b0 4b ff f9 ec ee a2 ef  |.nty.....K......|
00000010  02 37 39 79 c4 54 e8 7f  1f 03 02 85 5a 60 78 3f  |.79y.T......Z`x?|
00000020  f6 41 97 48 85 bc f0 19  f0 ca 2d b0 2b 09 60 1c  |.A.H......-.+.`.|
00000030  3d 1f 08 e3 cf 0f c4 a4  f8 9d 27 d7 f6 e5 ef 0d  |=.........'.....|
00000040  e2 0b 2c 35 ab b8 5f ec  56 b3 a3 2e a0 05 83 c7  |..,5.._.V.......|
00000050  ba a7 60 2f 3b b4 e5 75  b5 ba 3f 75 f7 dd f7 ad  |..`/;..u..?u....|
00000060  ac 05 2f ce 75 13 3a 28  92 ec 95 bd 0e 98 ad cb  |../.u.:(........|
00000070  38 4b 81 b0 f2 94 1e 03  f8 b0 44 05 28 07 81 ed  |8K........D.(...|
00000080  4c 0c 36 57 55 24 f9 6a  c5 b3 20 df 0a 49 5c 65  |L.6WU$.j.. ..I\e|
00000090  30 30 e7 44 b0 84 10 5b  57 44 11 d8 96 d3 4c 45  |00.D...[WD....LE|
000000a0  ca d5 0e 4b 1b 02 44 01  8c 49 05 00 94 10 c1 9b  |...K..D..I......|
000000b0  12 55 09 4c a7 d1 0e b3  f1 fb 3e 2a 0f 36 af df  |.U.L......>*.6..|
000000c0  01 16 82 80 98 0c 3c 2e  4a 9c b8 b8 18 15 63 c6  |......<.J.....c.|
000000d0  d5 68 06 68 3c 14 02 f7  61 61 6d aa 4b 74 ae 2e  |.h.h<...aam.Kt..|
000000e0  83 61 00 a6 82 b1 84 0a  7e b5 37 c4 48 8d 04 67  |.a......~.7.H..g|
000000f0  e9 5f c3 55 de 18 c1 7b  2d 8d 62 52 59 cd 02 96  |._.U...{-.bRY...|
00000100  21 6c b0 fc 65 16 a1 14  03 86 e7 82 9c 11 0f 81  |!l..e...........|
00000110  4a 05 3c 56 28 08 0d 17  aa 06 02 bf 88 7c 01 3e  |J.<V(........|.>|
00000120  f1 5f ca b8 2e 08 40 cc  83 c4 7f ee 0f 99 00 5a  |._....@........Z|
00000130  b6 6a 4a 0a a7 2a 1c c0  61 8b 86 40 67 04 a0 72  |.jJ..*..a..@g..r|
00000140  03 a3 c8 d0 86 0c c8 fd  bb c4 d4 0f 7a cc 02 2a  |............z..*|
00000150  d9 83 80 60 cc 58 c2 d0  1f 12 18 08 23 a6 47 8a  |...`.X......#.G.|
00000160  ee e7 9b 99 54 e7 14 e5  f6 cd 96 75 64 03 07 92  |....T......ud...|
00000170  d6 a8 d0 73 c6 c5 a0 6c  18 22 3f 95 b2 3c be 62  |...s...l."?..<.b|
00000180  29 d6 76 7a 78 0a e9 b5  11 09 e0 d2 0f 01 04 c8  |).vzx...........|
00000190  8c 24 88 c0 18 3d 82 5b  0d a6 1c 89 6a 58 f3 73  |.$...=.[....jX.s|
000001a0  85 43 8c 2b 13 84 45 65  c1 08 4a 1e b5 30 78 20  |.C.+..Ee..J..0x |
000001b0  ff a1 db 2d 8d a4 0e 33  32 0d c8 42 80 f9 00 fe  |...-...32..B....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


 
```

---

### Post by MadTeaParticipant on 2011-06-04
as far as i know, nothing was updated before the computer was turned off. (though I wasn't the last to use it...I can't be certain)

---

### Post by MadTeaParticipant on 2011-06-04
any suggestions out there?

---

### Post by Quackers on 2011-06-04
And all this happened when you turned your computer on? What did you do before you turned it off?
You have a Windows XP partition (sda1) which has XP boot files in it. It also has one of the Ubuntu boot files in there too, which is not a great start. But it gets worse.
sda2 is an extended partition which holds one logical partition -  a swap partition. No Ubuntu system at all!
And worse!
sda1 overlaps with sda2 and sda5.
This is not good!
Do you have backups?

---

### Post by MadTeaParticipant on 2011-06-04
this is why I have been so confused! I don't know what happened...I noticed the windows files and am confused because I thought they were overwritten when I installed ubuntu. Seems my hard drive is all wonky...It's a mess. 
The other partitions won't mount either...

---

### Post by MadTeaParticipant on 2011-06-04
the computer was hibernating all day and wouldn't respond when I got home, so I pressed the button to turn it off. when I turned it back on this is what happened. Might be time for testdisk

---

