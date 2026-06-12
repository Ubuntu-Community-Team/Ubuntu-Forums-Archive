---
title: "Unknown Bootloader - Boot Info Script and other Grub questions"
date: 2010-04-13
forum: General Help
---

### Post by BrokeMahPC on 2010-04-13
Just ran the Boot Info Script - useful item from sourceforge and came up with some questions that needed clarification. Hope you can help.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Last entry shows an unknown boot loader on sda2
I have 2 hard disks, dual booting with Windows XP
1stHD
sda1 = XP
sda2= Extended partition with sda5 Linux Mint 8 and sda6 Swap
I did have another partition with a linux install - deleted that partition and it is now just unallocated space - was going to tidy that up at some point.
2nd HD
sdb3 - Extended partition with Lucid 10.04 plus other storage partitions

Questions:
What is the Unknown boot loader - the windows boot loader?
Is it normal for it to be on the extended Linux partition - sda2?
I thought it would be on sda or sda1.
I have no Grub2 on Sdb - would it be wise to install it here also?
I would like to make 10.04 my main OS - could I install grub 2 on Sdb and then change this disk to boot 1st in the bios?

```
===== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  de 09 a8 b4 b7 90 0f 79  50 74 73 8b e8 e6 41 c1  |.......yPts...A.|
00000010  2f 35 c0 dc 5f fa 3d 4a  06 e9 3e f8 fc 7d 1d 6f  |/5.._.=J..>..}.o|
00000020  d2 c1 c6 af 3d b4 cb 94  83 51 d2 47 d6 cb c7 df  |....=....Q.G....|
00000030  93 e8 bc 7b 4a c5 c0 9c  11 aa 9a cd 10 fc 25 de  |...{J.........%.|
00000040  e9 2b 10 21 ce 33 4b f6  cd 32 89 df e4 14 6b 84  |.+.!.3K..2....k.|
00000050  97 f5 0e 83 8d 43 09 ef  10 2b f9 f3 cb 6b 8f 96  |.....C...+...k..|
00000060  79 b7 0d 2d 63 d2 e6 f7  89 ef d0 02 b9 49 9b cc  |y..-c........I..|
00000070  bb bf 8b 90 32 7e ef 6c  5c 55 4d d4 f8 c6 64 9d  |....2~.l\UM...d.|
00000080  a8 b1 bf d0 20 39 4f 27  6a 64 97 ce 88 e1 ea 92  |.... 9O'jd......|
00000090  a1 39 f1 16 a9 c6 7f e6  7c 95 1a fc ac 37 e3 b3  |.9......|....7..|
000000a0  3e 50 a1 8b 33 2d 41 7a  85 bc 93 59 a8 9c fb f3  |>P..3-Az...Y....|
000000b0  ce 04 f2 9a 64 29 8a 76  a3 5a b4 1b 75 ef 11 de  |....d).v.Z..u...|
000000c0  c0 e1 56 ba 51 bb 46 f8  ff 05 82 c9 fa 85 5e f6  |..V.Q.F.......^.|
000000d0  a9 a9 96 77 c3 c8 bd 8d  b7 f6 70 04 6a 53 50 b4  |...w......p.jSP.|
000000e0  1f f4 20 6f 0c b7 42 32  f1 4d a8 6c 54 c9 76 8e  |.. o..B2.M.lT.v.|
000000f0  83 51 3f 80 e7 d9 22 1a  fb 52 04 c2 b1 d0 e2 37  |.Q?..."..R.....7|
00000100  d0 e2 7f 3a 0b 38 cc 8b  70 b0 86 34 1d 9d db 6b  |...:.8..p..4...k|
00000110  81 f0 5d 96 1f 75 de b4  fb 20 e2 17 50 79 49 04  |..]..u... ..PyI.|
00000120  cd 12 01 8f 1a a0 eb df  e6 a3 56 4a 09 b7 18 af  |..........VJ....|
00000130  63 4f 7e 8f cb 73 54 7b  4e bb 27 b2 f1 eb d8 6a  |cO~..sT{N.'....j|
00000140  51 9f 74 e9 5f ce a6 67  6b a8 0b 27 ac 40 2e 67  |Q.t._..gk..'.@.g|
00000150  19 31 55 fb e9 ab 16 e9  ab 8e 86 aa 99 bb 29 9e  |.1U...........).|
00000160  e3 97 71 a8 5b 7f 22 32  02 5b c3 4e 14 20 1f a4  |..q.[."2.[.N. ..|
00000170  6d 72 4a 6b ec d7 ef 74  8d 5d a3 6f ac c9 1e 33  |mrJk...t.].o...3|
00000180  8e 6f 62 aa be a7 af 7a  76 9a ae ea 6a 3b 8e 03  |.ob....zv...j;..|
00000190  96 92 58 02 c5 f5 2f b1  f3 ea d8 0e 01 76 bf ce  |..X.../......v..|
000001a0  aa 01 0d 68 aa d8 fc 6f  a3 e6 6b d8 77 d1 1f 7d  |...h...o..k.w..}|
000001b0  89 be b3 37 f4 9d dd 0a  9d d9 33 99 33 0b 00 fe  |...7......3.3...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 2d 8d 01 05 00 fe  |..........-.....|
000001d0  ff ff 05 fe ff ff 32 5e  2c 06 30 85 4a 00 00 00  |......2^,.0.J...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```Edit More info
Just seen this post:
[http://ubuntuforums.org/showthread.php?t=1448970&highlight=unknown+bootloader](http://ubuntuforums.org/showthread.php?t=1448970&highlight=unknown+bootloader)
lindsay7 has 4 unknown MBRs

Also found this in the bootscript log which may be of use?
```
sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:
```

---

### Post by oldfred on 2010-04-13
You just have some data in the partition boot sector/record (PBR). Sometimes you can tell it is another boot loader. The script attempts to match bytes with known boot loaders but does not identify all. Yours just looks like random data. Normally data should not be written into that sector. Do you have any partition problems?

I like to have different operating systems on different drives and that operating systems boot loader in the MBR of that drive. I boot grub/ubuntu as grub2 has been very good at finding other systems. But I have customized mine as I have several more systems and the menu gets too large without some modification.

My extended partitions have all fields blank, perhaps the script found some data in the PBR of the extended. The extended is a primary partition, just that it is modified to be a container for logical partitions.

---

### Post by BrokeMahPC on 2010-04-13
Never had a partition problem till this - additional info - Gparted on a Mint 8 live CD showed a warning triangle over the one of the partitions in that extended partition. Gparted on a Lucid live CD shows no warnings.

Thanks for your help - I don't think it's anything to worry about. From  the advice here and elsewhere - as soon as I have time I will nuke that  extended partition with GParted and get rid of everything except windows  on that drive. It's been in use for awhile so could do with some  maintenance.

It is odd though - I have used GParted (never use anything else) many  times on that drive and not had a problem till this week. Whatever it is  may have occurred between 10.9.2009 when I last used parted (Mint Helena) and now - difficult to tell.

I will install Lucid again just for fun and see if anything happens.

---

