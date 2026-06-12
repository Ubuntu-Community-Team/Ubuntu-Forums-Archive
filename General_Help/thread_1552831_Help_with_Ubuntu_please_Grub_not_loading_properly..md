---
title: "Help with Ubuntu please? Grub not loading properly."
date: 2010-08-14
forum: General Help
---

### Post by dsmi147 on 2010-08-14
Hi guys, this is my first post here. Just writing here to work out what is wrong with my friends laptop. Any help would be much appreciated.
So I installed Ubuntu 10.04 lynx on it a couple months ago alongside the existing Windows Vista, and it has all been running fine until a couple days ago when it all went hay-wire.

So basically one time when I tried to start Ubuntu, it froze on the loading screen. This has happened from time to time so didn't think much of it. I just did a hard reset and tried to start the computer again like I occasionally have done.
But this time the grub OS selection screen didn't even come up, it just went straight to a black screen with the following written:

error: unknown filesystem

grub rescue>


Every time I start the computer now it comes up with the same thing.

I did a quick search on here and found a couple similar threads but nothing like this. Sorry if this has been posted before. What surprises me is that this wasn't an installation problem, but this happened seemingly for no reason at all. The day before the computer was running like a little champ :D, and now it won't even start :confused:.

I've got the Ubuntu install CD used, which I tried booting off. It let me "try Ubuntu" to get into the computer. Once on the computer, I had no idea how to go about fixing the problem.

I'm not too sure what the different parts of the hard drive are called on the computer or which one has linux installed on it, but I most likely chose the standard choice during installation if that helps.

Well thanks for reading, sorry if I wrote too much. If you have any ideas about how to fix it,  that would be great.

---

### Post by Rubi1200 on 2010-08-14
Hi and welcome to the forums :)

There could be a number of reasons why this has happened.

In order to rule out problems with GRUB, please boot the computer with the CD and choose live mode.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here.

We also need to know what your computer specifications are, especially RAM and graphics card.

---

### Post by dsmi147 on 2010-08-14
Thanks very much for the quick reply, I ran that script as you said. Here are the results:

Also the computer is an ASUS F5 laptop, 512MB of RAM, Intel Duo T2080 processor, ATI radeon Xpress 1100 graphics card. I did previously have the ATI driver updates installed and all seemed to be working well.


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
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    10,242,047    10,240,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     10,242,048   104,022,015    93,779,968   7 HPFS/NTFS
/dev/sda3         104,024,062   156,301,311    52,277,250   f W95 Ext d (LBA)
/dev/sda5         104,024,064   127,589,997    23,565,934   7 HPFS/NTFS
/dev/sda6         127,590,400   155,000,831    27,410,432  83 Linux
/dev/sda7         155,002,880   156,301,311     1,298,432  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        9417-721B                              vfat       RECOVERY                      
/dev/sda2        921C1A841C1A638F                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        76C81E46C81E0551                       ntfs       DATA                          
/dev/sda7        4e7c9ca8-84ed-4829-8e77-ff6f64205d2d   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  a6 0e 00 00 b6 0e 00 00  c6 0e 00 00 d6 0e 00 00  |................|
00000010  e6 0e 00 00 f6 0e 00 00  06 0f 00 00 16 0f 00 00  |................|
00000020  26 0f 00 00 36 0f 00 00  46 0f 00 00 56 0f 00 00  |&...6...F...V...|
00000030  66 0f 00 00 76 0f 00 00  86 0f 00 00 96 0f 00 00  |f...v...........|
00000040  26 10 00 00 36 10 00 00  46 10 00 00 56 10 00 00  |&...6...F...V...|
00000050  66 10 00 00 76 10 00 00  86 10 00 00 96 10 00 00  |f...v...........|
00000060  a6 0f 00 00 b6 0f 00 00  c6 0f 00 00 d6 0f 00 00  |................|
00000070  e6 0f 00 00 f6 0f 00 00  06 10 00 00 16 10 00 00  |................|
00000080  a6 10 00 00 b6 10 00 00  c6 10 00 00 d6 10 00 00  |................|
00000090  e6 10 00 00 f6 10 00 00  06 11 00 00 16 11 00 00  |................|
000000a0  26 11 00 00 36 11 00 00  46 11 00 00 56 11 00 00  |&...6...F...V...|
000000b0  b0 30 00 00 03 00 00 00  6c 69 62 6d 6d 2d 70 6c  |.0......libmm-pl|
000000c0  75 67 69 6e 2d 6e 6f 6b  69 61 2e 73 6f 00 00 00  |ugin-nokia.so...|
000000d0  b7 9e f6 2b 00 2e 73 68  73 74 72 74 61 62 00 2e  |...+..shstrtab..|
000000e0  6e 6f 74 65 2e 67 6e 75  2e 62 75 69 6c 64 2d 69  |note.gnu.build-i|
000000f0  64 00 2e 67 6e 75 2e 68  61 73 68 00 2e 64 79 6e  |d..gnu.hash..dyn|
00000100  72 73 69 6f 6e 5f 72 00  2e 72 65 6c 2e 64 79 6e  |rsion_r..rel.dyn|
00000110  00 2e 72 65 6c 2e 70 6c  74 00 2e 69 6e 69 74 00  |..rel.plt..init.|
00000120  73 79 6d 00 2e 64 79 6e  73 74 72 00 2e 67 6e 75  |sym..dynstr..gnu|
00000130  2e 76 65 72 73 69 6f 6e  00 2e 67 6e 75 2e 76 65  |.version..gnu.ve|
00000140  2e 74 65 78 74 00 2e 66  69 6e 69 00 2e 72 6f 64  |.text..fini..rod|
00000150  61 74 61 00 2e 65 68 5f  66 72 61 6d 65 00 2e 63  |ata..eh_frame..c|
00000160  74 6f 72 73 00 2e 64 74  6f 72 73 00 2e 6a 63 72  |tors..dtors..jcr|
00000170  00 2e 64 79 6e 61 6d 69  63 00 2e 67 6f 74 00 2e  |..dynamic..got..|
00000180  67 6f 74 2e 70 6c 74 00  2e 64 61 74 61 00 2e 62  |got.plt..data..b|
00000190  73 73 00 2e 67 6e 75 5f  64 65 62 75 67 6c 69 6e  |ss..gnu_debuglin|
000001a0  6b 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |k...............|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  24 00 00 00 00 00 00 00  00 00 00 00 04 00 00 00  |$...............|
000001d0  00 00 00 00 22 00 00 00  05 00 00 00 02 00 00 00  |...."...........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 0b 00 00 00  |................|
000001f0  07 00 00 00 02 00 00 00  f4 00 00 00 f4 00 00 00  |................|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by Rubi1200 on 2010-08-14
Hi,
thanks for getting the results back here.

Well, almost everything looks normal except for this:
> Mounting failed:
mount: unknown filesystem type ''

sda6 is your Linux partition, but it is not being mounted, which is why you are unable to boot into it.

I am unsure how to resolve this right now, although of course I know it can be done.

Hang in there and hopefully someone will come along and offer a solution soon.

Thanks. 

:)

---

