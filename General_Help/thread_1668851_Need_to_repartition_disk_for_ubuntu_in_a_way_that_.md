---
title: "Need to repartition disk for ubuntu in a way that won't kill windows"
date: 2011-01-16
forum: General Help
---

### Post by aflyingturtle on 2011-01-16
Theres going to be a long and short version of this post.

Short Version: Ubuntu got screwed up. Decided to remove the ubuntu partition by using the windows xp partitioner. Didn't realize it would screw up grub. Restored the xp boot using the xp installation cd. Now the only way to partition for Ubuntu is to reformat the whole drive. Any ways around this? Or do I have to backup xp, restore xp from its installation disk, restore xp, and then partition for ubuntu?

Long Version: So I originally had a windows xp computer. I tried ubuntu and liked it, so I installed Ubuntu, giving it a three GB partition. Since Ubuntu is about two and a half GB, I ran out of memory after my first download. So then I used Gparted and made the windows partition smaller. Since I was running Gparted from the ubuntu installed version, I had to make a live cd in order to resize ubuntu. I made a live cd from the website Gparted gave me (not knowing the default ubuntu live cd comes with Gparted) and made the cd. I ran it, but whenever I opened Gparted it crashed for unknown reasons. So I decided to go back to Ubuntu and make another cd, however ubuntu's theme had changed to something weird that I hadn't done. It also said there was a default configuration error with Gnome Power. Since I hadn't installed much to ubuntu yet, I figured I'd just uninstall it and install it with a larger Partition. I used the windows xp partitioner and deleted the Ubuntu partion. Rebooted, and realized I had broken grub accidentaly by doing this. I used a windows xp installation cd to fix the xp bootup. Went fine. Now however, When I try to install ubuntu the only option is to make a new partition table for the disk, Which would wipe the disk. So from the live cd I went to Gparted and looked at the partitions. The only partition is now SDA, which is unallocated it says. So what is the easiest possible way to reinstall ubuntu alongside windows? The only way I can think of (Which I'm not sure works) Is to backup windows, Reinstall windows with it's cd, Then restore the windows stuff, then partition Ubuntu. If theres an easier way I would really like to hear it. And please tell me if my way would work. I hope I can reinstall ubuntu somehow cause I love it.

---

### Post by amsterdamharu on 2011-01-16
Could you start the live CD and run the [boot info script]("http://sourceforge.net/projects/bootinfoscript/") and post it here?

I can then advice you how to partition.

When pasting it here please wrap it in &#91;code] &#91;/code] tags. In other words: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by aflyingturtle on 2011-01-16
Ubuntu doesn't have a specified program to run it. What should I run it as?

Edit: Sorry didn't realize it was a readme within itself. For whatever reason I can't run it using ```
sudo bash boot_info_script055.sh
``` because it says the file or directory doesn't exist

---

### Post by aflyingturtle on 2011-01-16
Double Stupid... Was in the main directory not downloads where it was installed... New to cmd line... anyway

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   141,049,855   141,049,793   7 HPFS/NTFS
/dev/sda2         149,420,030   156,301,311     6,881,282   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5     ?   576,238,802   971,203,391   394,964,590  2b Unknown

/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda2

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        7B6970B23E920A3F                       ntfs       Windows                       
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
error: /dev/sda5: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  07 45 62 37 c9 39 99 74  2c 64 60 ec 81 ab 0e 75  |.Eb7.9.t,d`....u|
00000010  70 9f f0 81 d4 2e 55 e2  dd af c4 9d 1a 46 b2 5a  |p.....U......F.Z|
00000020  91 67 92 68 da a1 26 6a  4a 6a 22 f2 26 01 2b ac  |.g.h..&jJj".&.+.|
00000030  cd 90 85 86 b0 5f 36 97  5c 94 f0 59 2d b6 4d 46  |....._6.\..Y-.MF|
00000040  cf 24 e6 fb 6e 45 86 d8  38 bf 91 2b 4f 9f 11 af  |.$..nE..8..+O...|
00000050  a4 eb 05 9f 30 b6 a9 61  50 f3 a7 88 3b b4 f1 b7  |....0..aP...;...|
00000060  1e 67 08 6a 12 be 00 7d  b4 10 10 59 af 9d 01 e3  |.g.j...}...Y....|
00000070  4c 88 a2 b1 74 54 0f 47  25 55 ef 46 bd 56 ff 7e  |L...tT.G%U.F.V.~|
00000080  a1 f6 3d c8 32 40 30 c1  15 f1 ec 85 ad ea 2d bb  |..=.2@0.......-.|
00000090  71 89 7b ae 21 f9 55 75  e7 46 0a af dd 3b b9 3f  |q.{.!.Uu.F...;.?|
000000a0  b5 75 5e 7f 92 5d f8 c1  f3 92 15 12 67 b2 66 39  |.u^..]......g.f9|
000000b0  31 74 77 1a 2f b0 f4 f5  71 7e bc 6b dd 80 f4 2d  |1tw./...q~.k...-|
000000c0  f5 44 21 7e 0a 15 36 1a  14 31 00 bf 8f b3 5d 9f  |.D!~..6..1....].|
000000d0  7f 0b dd 80 f1 60 86 8c  e2 e0 fb 71 ed d3 6b ca  |.....`.....q..k.|
000000e0  88 ff bf 44 f6 7b b4 4f  6f 72 44 8a 21 f7 1f 77  |...D.{.OorD.!..w|
000000f0  58 50 0e 21 19 44 98 0a  8b c4 11 52 88 58 bc 5a  |XP.!.D.....R.X.Z|
00000100  12 1a a5 e3 f6 96 e0 99  05 c5 94 9d d5 32 42 68  |.............2Bh|
00000110  9a 7b b6 9c 82 f0 f1 14  29 39 3e ca 22 d0 08 6f  |.{......)9>."..o|
00000120  dc 37 b4 38 2c 46 e1 7c  10 01 80 bb c8 39 4f 98  |.7.8,F.|.....9O.|
00000130  48 53 0c d7 b0 62 7c 55  7b 89 53 a8 f8 95 0e d4  |HS...b|U{.S.....|
00000140  03 ea 7b db b4 59 1d fc  13 b4 f9 2f 8a 4b 31 12  |..{..Y...../.K1.|
00000150  25 f8 59 74 fc 1f c9 cd  93 d5 4a 1f 4e ca f3 22  |%.Yt......J.N.."|
00000160  4e 6a a4 fa 73 0e 63 27  db a0 15 4c e7 24 5d 41  |Nj..s.c'...L.$]A|
00000170  c6 82 30 08 4d 74 8e 52  ab f7 7b 62 ad 66 f9 3a  |..0.Mt.R..{b.f.:|
00000180  13 66 44 86 89 9a 58 d2  41 f4 b1 e3 e5 9a ba e0  |.fD...X.A.......|
00000190  d9 3c 4e 81 fc ec 23 0a  9b ac 22 ca 11 58 e3 cf  |.<N...#..."..X..|
000001a0  d2 53 72 36 b2 63 9e 95  fa f2 ab b9 bb c8 b6 04  |.Sr6.c..........|
000001b0  53 f8 32 0b 9a 2e af a0  ee 1b 5b c6 98 0d 00 ef  |S.2.......[.....|
000001c0  ff ff 05 ef ff ff c3 9f  62 00 3f 60 06 00 00 00  |........b.?`....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory 
```

---

### Post by amsterdamharu on 2011-01-16
Ok, so your partitions are a bit messed up. The only partition you wish to keep is the Windows one so you can try the following:
```
sudo fdisk /dev/sda
```

Press d to delete
Press 3 to delete the extended partition
Press d to delete
press 2 to delete 
Press p to print a list, it should only show the ntfs Windows partition.
press w to write the new partition table to disk and exit

Now when you reboot you might have to run the Windows CD to fix bootloader again but maybe it'll be ok.

You can then boot from live CD again and try gparted to resize partitions, there is no guarantee it'll be without errors and you might loose your data. If something goes wrong don't try to boot Windows. Use the live CD to post here and try a program called testdisk to fix it again.

---

### Post by aflyingturtle on 2011-01-17
Did that. Rebooted onto ubuntu so I could use Gparted to shrink windows partition. I told it to and it had an error. Heres the detailed report. ```
 
GParted 0.6.2
 Libparted 2.3
    **Shrink /dev/sda1 from 67.26 GiB to 63.80 GiB**  00:02:33    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 141049855
size: 141049793 (67.26 GiB)[/I]          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:23    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 72217489920 bytes (72218 MB)
Current device size: 72217494016 bytes (72218 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 66254 MB (91.7%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     72218 MB             0
Multi-Record       :     72218 MB          3494
$MFTMirr           :      2579 MB             1
Compressed         :     69016 MB         93012
Ordinary           :     72216 MB         54917
You might resize at 66253328384 bytes or 66254 MB (freeing 5964 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             shrink file system  00:01:43    ( ERROR )             run simulation  00:01:43    ( ERROR )             ***ntfsresize -P --force /dev/sda1 -s 68502389247 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 72217489920 bytes (72218 MB)
Current device size: 72217494016 bytes (72218 MB)
New volume size    : 68502385152 bytes (68503 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 66254 MB (91.7%)
Collecting resizing constraints ...
Needed relocations : 855540 (3505 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (2176 > 1024), not yet supported!
Please try to free less space.
[/I]                check file system on /dev/sda1 for errors and (if possible) fix them  00:00:22    ( SUCCESS )             ***ntfsresize -P -i -f -v /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 72217489920 bytes (72218 MB)
Current device size: 72217494016 bytes (72218 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 66254 MB (91.7%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :     72218 MB             0
Multi-Record       :     72218 MB          3494
$MFTMirr           :      2579 MB             1
Compressed         :     69016 MB         93012
Ordinary           :     72216 MB         54917
You might resize at 66253328384 bytes or 66254 MB (freeing 5964 MB).
Please make a test run using both the -n and -s options before real resizing!
[/I]             grow file system to fill the partition  00:00:02    ( SUCCESS )             run simulation  00:00:02    ( SUCCESS )             ***ntfsresize -P --force /dev/sda1 --no-action***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 72217489920 bytes (72218 MB)
Current device size: 72217494016 bytes (72218 MB)
New volume size    : 72217489920 bytes (72218 MB)
Nothing to do: NTFS volume size is already OK.
[/I]             real resize  00:00:00    ( SUCCESS )             ***ntfsresize -P --force /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 72217489920 bytes (72218 MB)
Current device size: 72217494016 bytes (72218 MB)
New volume size    : 72217489920 bytes (72218 MB)
Nothing to do: NTFS volume size is already OK.[/I]
```

---

### Post by aflyingturtle on 2011-01-17
And just fyi Gparted reports that windows is the same size as before I told it to repartition. So the repartition was cancelled or something.

---

### Post by oldfred on 2011-01-17
It looks like it is saying that your windows is 91% full. When windows gets below 20% free it starts to slow down and at 10% just about stops working a it needs a lot of free space.

If gparted ran ntfsfix then you also need to run chkdsk from the windows CD and rerun until there are no errors.

If you do have some space to work in windows, houseclean  then also run defrag.

---

### Post by aflyingturtle on 2011-01-17
Doesn't windows automatically do a checkdisk on startup if it's suspicous of anything?

---

### Post by aflyingturtle on 2011-01-17
Nevermind. I ran it from the cd. So your saying I should delete some windows files I don't need so that I can shrink the partition because windows will refuse to give up below 10% free space?

---

### Post by oldfred on 2011-01-17
My XP would boot without any issue but gparted would not even see it. Then I ran chkdsk and gparted saw it, so no windows does not always run chkdsk when it should.

I am not sure windows prevents you, but I think gparted says it will not shrink any partition too small. Linux partitions hide some overflow space but also need space to work well.

---

### Post by Mark Phelps on 2011-01-18
If you use a Linux utility to "force" a shrinkage of an MS Windows OS partition that already has less than 10% free space, while the shrink might work, it's almost certainly going to leave you with an unbootable version of MS Windows.

Since you're planning on dual-booting, my guess would be that most of your Windows disk space is taken up by data files -- which you will want to share between Ubuntu and Windows later anyway.

So, you should move the data files you want to share to external storage, defrag the MS Windows partition, and then shrink it.

Later, after you've installed Ubuntu, you could create a shared data partition (recommend NTFS for this) and copy the data files back onto the drive into that partition.

---

### Post by aflyingturtle on 2011-01-20
Anyways. I ran a chksdsk from the windows cd, Repartitioned space for Ubuntu and did a successful clean install. Thanks for the help!

---

