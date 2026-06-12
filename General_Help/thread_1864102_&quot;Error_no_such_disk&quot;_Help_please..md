---
title: "&quot;Error: no such disk&quot; Help please."
date: 2011-10-18
forum: General Help
---

### Post by eddie3000 on 2011-10-18
Hello! I have seen many people with a similar problem, and lot's of them solving them, but not me!:(
I have installed Ubuntu Studio 10.04 alternate, I have 6 HDDs, of which two form a raid 0 array, another three form another raid 0 disk array and the sixth is on it's own. 

I have gone through this entire procedure three times and it all happens in the same manner.

At first all goes well. I get Ubuntu studio going. I then upgrade the kernel to fix the ram limitation as I have more than 3gb. It then seems to decide for whatever reason to update and install the grub bootloader on sdc, so I have to set that disk  in the bios as the first boot-up disk and it all works fine again. Then Ubuntu wants to install "upgrades", and after all the upgrades (>250MB of upgrades, and an hour or two) I get the "Error: no such disk" message when I boot and the grub rescue prompt. I does not matter which HDD I selecet in the bios, it won't work.

I have tried the supergrubfix2 cd, and that can't even detect an OS installed on the system. I'm using a live cd, ubuntu 10.04, and I can't mount the raid because the computer says "there aren't enough components to start the array". Many people around with similar problems but not quite this one I think. I'm no expert, so I haven't the faintest idea of how to get this fixed.

Here's the output text file from the boot info script if it may help:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md1)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md0)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Windows Vista/7
    Boot sector info:  

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   488,396,799   488,394,752  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048     7,813,119     7,811,072  fd Linux raid autodetect
/dev/sdb2           7,815,166   976,771,071   968,955,906   5 Extended
/dev/sdb5           7,815,168   976,771,071   968,955,904  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   488,396,799   488,394,752  fd Linux raid autodetect


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048     7,813,119     7,811,072  fd Linux raid autodetect
/dev/sdd2           7,815,166   976,771,071   968,955,906   5 Extended
/dev/sdd5           7,815,168   976,771,071   968,955,904  fd Linux raid autodetect


Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048     7,813,119     7,811,072  fd Linux raid autodetect
/dev/sde2           7,815,166   976,771,071   968,955,906   5 Extended
/dev/sde5           7,815,168   976,771,071   968,955,904  fd Linux raid autodetect


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7f1002fe-9045-60cb-c250-bda161d75cb0   linux_raid_member 
/dev/sdb1        afa8a5fb-ae39-ae22-84bc-dd4f2afe9031   linux_raid_member 
/dev/sdb5        949eb649-f9f9-f636-2933-ed2bf55026cc   linux_raid_member 
/dev/sdc1        7f1002fe-9045-60cb-c250-bda161d75cb0   linux_raid_member 
/dev/sdd1        afa8a5fb-ae39-ae22-84bc-dd4f2afe9031   linux_raid_member 
/dev/sdd5        949eb649-f9f9-f636-2933-ed2bf55026cc   linux_raid_member 
/dev/sde1        afa8a5fb-ae39-ae22-84bc-dd4f2afe9031   linux_raid_member 
/dev/sde5        949eb649-f9f9-f636-2933-ed2bf55026cc   linux_raid_member 
/dev/sdf1        dc69211b-be3c-4827-9f9f-8b5ee23b575a   ext4       backups

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 a8 b6  |............. ..|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 80 00 20  |........ ...... |
00000030  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d5 2d  |............. .-|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 bb 8c  |............. ..|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 60 2c  |............. `,|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 64 8e  |............. d.|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 bf 2e  |............. ..|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d1 8f  |............. ..|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0a 2f  |............. ./|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 da 8b  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 01 2b  |............. .+|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6f 8a  |............. o.|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b4 2a  |............. .*|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b0 88  |............. ..|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6b 28  |............. k(|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 05 89  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 de 29  |............. .)|
00000200

Unknown BootLoader on sdd5

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 cc 5f a8 1e  |........ ...._..|
00000010  14 00 04 00 00 00 00 00  00 00 00 00 a8 1e 56 bf  |..............V.|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 00 00 20  |........ ...... |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 ad fb  |............. ..|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 6f 01 00 20  |........ ...o.. |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 bf c3  |............. ..|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 69 04 00 20  |........ ...i.. |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 97 bb  |............. ..|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 ce 03 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b2 7f  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 1d 06 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b2 33  |............. .3|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 b8 05 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 1e 8d  |............. ..|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 e4 04 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 46 ff  |............. F.|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 2a 04 00 20  |........ ...*.. |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 c8 8c  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 af 02 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 c9 a8  |............. ..|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 ac 06 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 15 8c  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 68 06 00 20  |........ ...h.. |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 b3 21  |............. .!|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 06 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 2b ff  |............. +.|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 ad 00 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 a3 73  |............. .s|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 aa 02 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 dd c7  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 40 08 00 20  |........ ...@.. |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 34 e9  |............. 4.|
00000200

Unknown BootLoader on sde2

00000000  68 49 9c 01 e3 46 e4 6e  6f 71 a5 2b 2f 63 58 b0  |hI...F.noq.+/cX.|
00000010  bf 90 2c 5c 71 d7 dc 2e  8e d6 41 30 63 df 3c 9b  |..,\q.....A0c.<.|
00000020  e4 ee 6c f0 1e 92 cf a2  89 9f 75 0f 03 69 96 64  |..l.......u..i.d|
00000030  86 56 96 ad d5 22 57 6e  b3 96 d4 d6 54 00 70 fd  |.V..."Wn....T.p.|
00000040  8a fd c8 9d ca d6 dd 05  53 93 ef 98 2d 24 d2 3f  |........S...-$.?|
00000050  1a c5 ea 2a 0f 36 da 06  68 70 aa bb da ce 9c df  |...*.6..hp......|
00000060  6e bd 5f c2 63 22 69 28  66 3f c8 9f 02 f7 13 84  |n._.c"i(f?......|
00000070  05 75 19 4c ef c0 68 c3  f1 66 6b 08 af 6a bb ab  |.u.L..h..fk..j..|
00000080  12 8b 03 b5 35 d3 ff 0a  bc 0f 9e bd 78 4c 36 84  |....5.......xL6.|
00000090  a9 3a e6 ee 04 bd f6 86  bd 29 de 02 a0 78 fa 04  |.:.......)...x..|
000000a0  22 86 51 4b c1 a6 8f b8  aa df 72 33 be 2f cc 07  |".QK......r3./..|
000000b0  9c eb 41 a1 1f a2 46 05  1b 6d a5 a6 da 0d 2f dc  |..A...F..m..../.|
000000c0  42 6d 18 79 e3 86 39 11  2d 15 2e 1c 6b 1e cf a5  |Bm.y..9.-...k...|
000000d0  14 9a 69 61 25 8b 1f 9f  d8 a6 9b e5 b6 69 bb f1  |..ia%........i..|
000000e0  b9 58 cf 98 8b ec dd 31  dc 5b 1d eb b9 ea 18 ac  |.X.....1.[......|
000000f0  c4 de b3 3d d3 7d 9a 44  4b 79 8d 6c 6c 57 6a d0  |...=.}.DKy.llWj.|
00000100  5d 82 2c 2f 68 87 a4 8c  5c d4 25 72 6a 2b e6 8e  |].,/h...\.%rj+..|
00000110  cd df c6 a5 ef 75 21 d4  a8 9f 62 b3 c3 0f d5 3e  |.....u!...b....>|
00000120  3e 98 0c 99 f3 d0 3c cb  7c fa 7c 6d 70 4f 2a d7  |>.....<.|.|mpO*.|
00000130  32 93 bf 14 f8 9c 6d bb  2f 44 9e 2f b8 82 73 22  |2.....m./D./..s"|
00000140  7c 72 c7 05 18 09 54 91  64 18 32 e4 17 2e e8 a6  ||r....T.d.2.....|
00000150  29 30 9f 6a ca 21 54 f1  27 94 1a 60 7d b1 08 cd  |)0.j.!T.'..`}...|
00000160  26 1f 15 0c 78 81 49 89  a2 02 9a e2 29 5c 12 e5  |&...x.I.....)\..|
00000170  9b 13 74 7c bc a2 f6 75  63 2e 97 a9 2e d7 50 0b  |..t|...uc.....P.|
00000180  e9 5f 4f e1 70 fe c4 cf  e7 02 21 fa a6 ae 2f 8d  |._O.p.....!.../.|
00000190  bb 4b 55 a3 a6 ed 4b 33  9e 88 e7 d9 8b 96 34 f0  |.KU...K3......4.|
000001a0  dd 77 81 7d 8a bb 05 45  76 54 78 59 34 c3 7e f7  |.w.}...EvTxY4.~.|
000001b0  05 6a 27 2c 4b 42 2b 79  f3 ef 62 92 cf 23 00 78  |.j',KB+y..b..#.x|
000001c0  53 e6 fd fe ff ff 02 00  00 00 00 18 c1 39 00 00  |S............9..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sde5

00000000  00 00 c0 07 10 00 c0 07  20 00 c0 07 de 5f f9 1f  |........ ...._..|
00000010  01 00 04 00 00 00 00 00  00 00 00 00 f9 1f 7b 60  |..............{`|
00000020  01 00 c0 07 11 00 c0 07  20 02 c0 07 f8 07 00 20  |........ ...... |
00000030  00 00 05 00 00 00 00 00  00 00 00 00 00 20 f2 10  |............. ..|
00000040  02 00 c0 07 12 00 c0 07  20 04 c0 07 00 00 00 20  |........ ...... |
00000050  00 00 05 00 00 00 00 00  00 00 00 00 00 20 9f d1  |............. ..|
00000060  03 00 c0 07 13 00 c0 07  20 06 c0 07 00 00 00 20  |........ ...... |
00000070  00 00 05 00 00 00 00 00  00 00 00 00 00 20 44 71  |............. Dq|
00000080  04 00 c0 07 14 00 c0 07  20 08 c0 07 00 00 00 20  |........ ...... |
00000090  00 00 05 00 00 00 00 00  00 00 00 00 00 20 40 d3  |............. @.|
000000a0  05 00 c0 07 15 00 c0 07  20 0a c0 07 00 00 00 20  |........ ...... |
000000b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 9b 73  |............. .s|
000000c0  06 00 c0 07 16 00 c0 07  20 0c c0 07 00 00 00 20  |........ ...... |
000000d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 f5 d2  |............. ..|
000000e0  07 00 c0 07 17 00 c0 07  20 0e c0 07 00 00 00 20  |........ ...... |
000000f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 2e 72  |............. .r|
00000100  08 00 c0 07 18 00 c0 07  20 10 c0 07 00 00 00 20  |........ ...... |
00000110  00 00 05 00 00 00 00 00  00 00 00 00 00 20 fe d6  |............. ..|
00000120  09 00 c0 07 19 00 c0 07  20 12 c0 07 00 00 00 20  |........ ...... |
00000130  00 00 05 00 00 00 00 00  00 00 00 00 00 20 25 76  |............. %v|
00000140  0a 00 c0 07 1a 00 c0 07  20 14 c0 07 00 00 00 20  |........ ...... |
00000150  00 00 05 00 00 00 00 00  00 00 00 00 00 20 4b d7  |............. K.|
00000160  0b 00 c0 07 1b 00 c0 07  20 16 c0 07 00 00 00 20  |........ ...... |
00000170  00 00 05 00 00 00 00 00  00 00 00 00 00 20 90 77  |............. .w|
00000180  0c 00 c0 07 1c 00 c0 07  20 18 c0 07 00 00 00 20  |........ ...... |
00000190  00 00 05 00 00 00 00 00  00 00 00 00 00 20 94 d5  |............. ..|
000001a0  0d 00 c0 07 1d 00 c0 07  20 1a c0 07 00 00 00 20  |........ ...... |
000001b0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 4f 75  |............. Ou|
000001c0  0e 00 c0 07 1e 00 c0 07  20 1c c0 07 00 00 00 20  |........ ...... |
000001d0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 21 d4  |............. !.|
000001e0  0f 00 c0 07 1f 00 c0 07  20 1e c0 07 00 00 00 20  |........ ...... |
000001f0  00 00 05 00 00 00 00 00  00 00 00 00 00 20 fa 74  |............. .t|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdg 


```

I don't know how tricky it is to fix this, but if anybody knows about another linux distribution that can handle software raid on setup easily for dummies like myself I might consider changing. Nevertheless, fixing this would also be great.
Thanks!

---

### Post by eddie3000 on 2011-10-19
Hello?;):D

---

