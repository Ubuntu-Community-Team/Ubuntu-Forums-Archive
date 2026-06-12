---
title: "Formatted bootloader and windows partition"
date: 2011-06-24
forum: General Help
---

### Post by neo1786 on 2011-06-24
Hi, This might be the weirdest post u have come across.

I had a Windows 7 & Ubuntu 10.04 dual boot, installed from a Live CD,not using Wubi.

i was running a script to format a sd card. the script assumed the sd card to be on sdb while actually my 500GB hard drive was on sdb.

now i cant boot any OS, obviously! and get stuck at a grub rescue prompt. i want to kno if any data is recoverable. Also would it be possible ,somehow to get to the windows recovery partition?? here is my boot info script, if it is any help.
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     1,463,633     1,463,572  83 Linux
/dev/sdb2           1,463,634     2,927,267     1,463,634  83 Linux
/dev/sdb3           2,927,268     3,861,421       934,154  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  12 91 f2 60 90 a0 2f 19  01 00 00 00 85 00 67 68  |...`../.......gh|
00000010  46 50 3c a3 c4 4a ce 9f  c4 4a 32 00 ff ff 50 ed  |FP<..J...J2...P.|
00000020  12 00 18 ee 12 00 d6 7a  7c 00 ff ff ff ff 24 ee  |.......z|.....$.|
00000030  12 00 02 27 43 00 06 e8  c1 36 28 0a 00 00 02 00  |...'C....6(.....|
00000040  00 00 49 aa 80 7c 80 ee  12 00 00 ee 12 00 84 ee  |..I..|..........|
00000050  12 00 2a 7b 7c 00 ff 00  00 00 00 00 00 00 00 00  |..*{|...........|
00000060  00 00 00 00 00 00 00 00  00 00 00 57 44 43 20 57  |...........WDC W|
00000070  44 32 35 20 30 30 42 45  56 54 2d 32 36 5a 43 54  |D25 00BEVT-26ZCT|
00000080  30 20 31 32 2e 30 00 00  00 00 00 00 00 00 00 00  |0 12.0..........|
00000090  00 00 00 00 00 00 00 04  00 34 24 cc 9c 1f 00 00  |.........4$.....|
000000a0  28 1f 00 00 29 1f 00 00  2a 1f 00 00 2b 1f 00 00  |(...)...*...+...|
000000b0  2c 1f 00 00 2d 1f 00 00  2e 1f 00 00 2f 1f 00 00  |,...-......./...|
000000c0  30 1f 00 00 31 1f 00 00  32 1f 00 00 33 1f 00 00  |0...1...2...3...|
000000d0  34 1f 00 00 35 1f 00 00  36 1f 00 00 37 1f 00 00  |4...5...6...7...|
000000e0  38 1f 00 00 39 1f 00 00  3a 1f 00 00 3b 1f 00 00  |8...9...:...;...|
000000f0  3c 1f 00 00 3d 1f 00 00  3e 1f 00 00 3f 1f 00 00  |<...=...>...?...|
00000100  40 1f 00 00 41 1f 00 00  42 1f 00 00 43 1f 00 00  |@...A...B...C...|
00000110  44 1f 00 00 45 1f 00 00  46 1f 00 00 47 1f 00 00  |D...E...F...G...|
00000120  48 1f 00 00 49 1f 00 00  4a 1f 00 00 4b 1f 00 00  |H...I...J...K...|
00000130  4c 1f 00 00 4d 1f 00 00  4e 1f 00 00 4f 1f 00 00  |L...M...N...O...|
00000140  50 1f 00 00 51 1f 00 00  52 1f 00 00 53 1f 00 00  |P...Q...R...S...|
00000150  54 1f 00 00 55 1f 00 00  56 1f 00 00 57 1f 00 00  |T...U...V...W...|
00000160  58 1f 00 00 59 1f 00 00  5a 1f 00 00 5b 1f 00 00  |X...Y...Z...[...|
00000170  5c 1f 00 00 5d 1f 00 00  5e 1f 00 00 5f 1f 00 00  |\...]...^..._...|
00000180  60 1f 00 00 61 1f 00 00  62 1f 00 00 63 1f 00 00  |`...a...b...c...|
00000190  64 1f 00 00 65 1f 00 00  66 1f 00 00 67 1f 00 00  |d...e...f...g...|
000001a0  68 1f 00 00 69 1f 00 00  6a 1f 00 00 6b 1f 00 00  |h...i...j...k...|
000001b0  6c 1f 00 00 6d 1f 00 00  6e 1f 00 00 6f 1f 00 00  |l...m...n...o...|
000001c0  70 1f 00 00 71 1f 00 00  72 1f 00 00 73 1f 00 00  |p...q...r...s...|
000001d0  74 1f 00 00 75 1f 00 00  76 1f 00 00 77 1f 00 00  |t...u...v...w...|
000001e0  78 1f 00 00 79 1f 00 00  7a 1f 00 00 7b 1f 00 00  |x...y...z...{...|
000001f0  7c 1f 00 00 7d 1f 00 00  7e 1f 00 00 7f 1f 00 00  ||...}...~.......|
00000200

Unknown BootLoader on sdb2

00000000  8f ef 8c b7 23 8d f6 9d  da 9a 1a f8 47 87 2b 2e  |....#.......G.+.|
00000010  07 a0 7f 34 bb 5e e6 e2  22 e2 6c 0e c7 70 96 5e  |...4.^..".l..p.^|
00000020  98 e7 f6 2f 5e b4 9a ee  cf da b4 97 48 bd 23 7f  |.../^.......H.#.|
00000030  49 a0 79 90 de 16 23 10  07 4f df 7d 1c fd 55 8c  |I.y...#..O.}..U.|
00000040  22 0a 86 8e 8e 9a 8d eb  f6 f4 47 b4 c3 44 df 4e  |".........G..D.N|
00000050  79 54 d1 f4 1e 0b 0a 9f  1b 7c 30 47 2f cc 94 31  |yT.......|0G/..1|
00000060  93 cb 56 1b 53 66 25 3a  fc 78 df af 04 0a 5f 21  |..V.Sf%:.x...._!|
00000070  28 6a b6 38 f2 a3 73 3a  52 dc 6c 5b d3 83 39 c6  |(j.8..s:R.l[..9.|
00000080  94 92 b2 e7 23 cb 56 b7  a7 79 4f ba 9c 8b 08 56  |....#.V..yO....V|
00000090  8c 7b a8 2e 91 3e 25 93  c6 32 aa 2f 5c 46 86 0d  |.{...>%..2./\F..|
000000a0  ea 27 93 92 79 f8 f0 a1  65 54 6f 3c cf 6d fe 19  |.'..y...eTo<.m..|
000000b0  fc 48 03 91 88 67 98 ae  b7 b4 8d 09 2e ca 1e 4e  |.H...g.........N|
000000c0  53 96 6c 53 72 78 54 54  15 9e 83 2b e0 39 89 e7  |S.lSrxTT...+.9..|
000000d0  e0 f2 4c 54 e0 78 30 c8  3e 8c 75 f6 7c c0 33 41  |..LT.x0.>.u.|.3A|
000000e0  f4 d3 66 24 8a 15 7b 36  0e 67 5d fb dc f9 67 e8  |..f$..{6.g]...g.|
000000f0  3b 4c b1 7c 4a 50 1d 4d  f3 e6 37 47 ba 41 6f ee  |;L.|JP.M..7G.Ao.|
00000100  dc 79 99 a8 6f 14 d3 15  62 81 cf cb 9c fb 89 4d  |.y..o...b......M|
00000110  94 1f 3e b0 dd 6a 04 bd  e7 0a af 07 a3 69 7e 15  |..>..j.......i~.|
00000120  5f 56 96 2f 23 bc 82 1a  43 01 af bb f4 f3 6e d0  |_V./#...C.....n.|
00000130  3b e5 8b 78 db 45 7a e1  aa 92 80 18 f8 c4 d9 41  |;..x.Ez........A|
00000140  4f 07 3d 87 c6 88 2c 93  b3 6b b8 22 5c 1c c2 a3  |O.=...,..k."\...|
00000150  1e a3 17 f0 85 b6 d1 ad  80 3e 71 d0 0f 38 b4 f7  |.........>q..8..|
00000160  17 cd 9c 5d 24 aa ea 31  4e 0e 0f 7a 38 f9 84 96  |...]$..1N..z8...|
00000170  ed 42 f0 a7 29 9f af 9d  b3 7b 88 04 7c bc 97 d1  |.B..)....{..|...|
00000180  29 97 17 f8 63 c6 87 5b  01 a3 5a c5 c9 38 cf 3b  |)...c..[..Z..8.;|
00000190  dc f5 4d e0 96 66 b6 06  fc f2 87 39 5f 9a e4 e4  |..M..f.....9_...|
000001a0  a0 8a d1 5b 80 cd de eb  f6 7b fc b2 95 3b 59 4e  |...[.....{...;YN|
000001b0  ce 09 46 ce e0 ef 7c ad  bf e1 e2 2e da 22 6d 11  |..F...|......"m.|
000001c0  40 66 3c 34 ce cd df f8  a7 9f 70 7e 6b 03 7d 64  |@f<4......p~k.}d|
000001d0  84 0f b0 ac 1f b0 ab e1  f0 12 cc 27 c3 c7 32 90  |...........'..2.|
000001e0  ff a2 6a f5 53 9c 7c d9  55 27 c6 ef c6 66 7d 10  |..j.S.|.U'...f}.|
000001f0  fe 44 f9 5d f5 0f 21 af  28 d6 ad 93 df 3d 0f ca  |.D.]..!.(....=..|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sda 




```

---

### Post by neo1786 on 2011-06-24
no replies yet? does this mean its not possible to recover anythng? plz guys, reply !

---

### Post by LordNeo on 2011-06-24
Recover data? Posible but not easy to do.
Recover grub? Piece of cake, just boot into a LiveCD and follow the steps on the Grub guide (first result typing "restore grub" in google)

---

### Post by neo1786 on 2011-06-24
thank you for replying..

```

grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3

```

```

sudo grub
sudo: grub: command not found


```

i dont kno y it is so..

---

### Post by LordNeo on 2011-06-24
Boot from LiveCD
Type:
sudo fdisk -l

This will show wich partition has Linux.

Then type:

sudo mount /dev/sda1 /mnt

(switch "sda1" accordingly)

Then:
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt

Now you are "logged" into your base system

Type:

grub-install --recheck /dev/sda
sudo update-grub

Done. Reboot and check

---

### Post by neo1786 on 2011-06-24
fdisk -l return no result :(

---

### Post by Rubi1200 on 2011-06-24
The boot script results indicate serious damage to sdb:
> Mounting failed:   mount: unknown filesystem type
**Attempting to write any data to the drive will simply exacerbate the problem.**

Stop all read/write activity and use a LiveCD to boot the computer.

Then install Testdisk and see if you can recover the partitions:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by neo1786 on 2011-06-24
```
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ 

```

thts wat i mean

---

### Post by LordNeo on 2011-06-24
did you used "sudo" before?
It should return your partition table

---

### Post by neo1786 on 2011-06-24
thanks for the reply..im on a live CD rite now

---

### Post by neo1786 on 2011-06-24
```

sudo fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6eb45a1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          92      731786   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              92         183      731817   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sdb3             183         241      467077   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.


```

---

### Post by LordNeo on 2011-06-24
Then your linux partition is sdb2. Follow the steps on my previous post using "sdb2" instead of "sda1" and "sdb" instead of "sda".

EDIT:

Boot from LiveCD <--- DONE
Type:
sudo fdisk -l <--- DONE

This will show wich partition has Linux. <--- DONE

Then type:

sudo mount /dev/sdb2 /mnt

Then:
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

Now you are "logged" into your base system

Type:

grub-install --recheck /dev/sdb
sudo update-grub

Done. Reboot and check

---

### Post by Rubi1200 on 2011-06-24
> **LordNeo said:**
> Then your linux partition is sdb2.
On what basis have you determined this?

Did you read my first post?

---

### Post by neo1786 on 2011-06-24
```
sudo mount /dev/sdb2 /mnt
mount: you must specify the filesystem type

```

---

### Post by neo1786 on 2011-06-24
> **Rubi1200 said:**
> On what basis have you determined this?

Did you read my first post?

I did, im downloading test disk rite now...im grateful to both of u for helping me out here. whose advice should i follow??

---

### Post by LordNeo on 2011-06-24
> **Rubi1200 said:**
> On what basis have you determined this?

Did you read my first post?

Did you saw the fdisk output or not?

Also, in your script thing output looks like that sda is not even recognized, so the chances are he formated his sda drive (probably with Windows on it, due the fact there is no FAT/NTFS partition on sdb) and the sdb is more or less ok.

@OP: Follow Rubi1200's advices, i'm off

---

### Post by neo1786 on 2011-06-24
im running testdisk rite now.

---

### Post by neo1786 on 2011-06-24
This is my output after hitting anaylse
```

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

No ext2, JFS, Reiser, cramfs or XFS marker
 1 * Linux                    0   0 63    91  27 18    1463572
 1 * Linux                    0   0 63    91  27 18    1463572
No ext2, JFS, Reiser, cramfs or XFS marker
 2 P Linux                   91  27 19   182  54 36    1463634
 2 P Linux                   91  27 19   182  54 36    1463634
 3 P Linux Swap             182  54 37   240  92 26     934154
 3 P Linux Swap             182  54 37   240  92 26     934154

```

---

### Post by Quackers on 2011-06-24
Whatever you can do to recover the situation can be done from the live cd desktop. As Rubi1200 has said you must stop using the installed system for the moment, as you risk over-writing data on it.
I don't know what's happened exactly there. If you open gparted does it see the partitions? If so, please right-click on each one and select "check" and see if any errors are reported.
Other than that I think Rubi1200's idea regarding testdisk is just about your best bet.
Good luck.

---

### Post by neo1786 on 2011-06-24
I followed the testdisk instructions, wrote the new partition table, restarted the machine, get the same grub rescue prompt. Im in the live CD now

```
 sudo fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6eb45a1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         192     1536000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2             192       30583   244120540   83  Linux
/dev/sdb3           30583       58131   221279232   83  Linux
/dev/sdb4           58132       60802    21454807+   f  W95 Ext'd (LBA)
/dev/sdb5           58132       59301     9390072   82  Linux swap / Solaris
/dev/sdb6           59301       60802    12058624    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

``` 

I think the last partition is the Windows recovery.
What i want to do is, put windows back up again...then install Ubuntu to dual boot as before.

---

### Post by Rubi1200 on 2011-06-24
Please run the boot info script again so we can see what has changed and post the results here.

---

### Post by neo1786 on 2011-06-24
The new boot script info

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     3,074,047     3,072,000  83 Linux
/dev/sdb2           3,074,048   491,315,127   488,241,080  83 Linux
/dev/sdb3         491,315,200   933,873,663   442,558,464  83 Linux
/dev/sdb4         933,874,515   976,784,129    42,909,615   f W95 Extended (LBA)
/dev/sdb5         933,875,712   952,655,855    18,780,144  82 Linux swap / Solaris
/dev/sdb6         952,655,872   976,773,119    24,117,248   7 NTFS / exFAT / HPFS

/dev/sdb4 ends after the last sector of /dev/sdb

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        9e9326fe-03b2-4ff5-ba54-f936047cb0ad   ext3       Main
/dev/sdb2        3abaddb0-af79-42d7-bb6e-692e39c73676   ext3       Reserve
/dev/sdb3        c44f2607-cfcd-4518-bcdd-2879d5f831fb   ext4       
/dev/sdb5        4b458626-0b3c-4371-abae-7875c6a230e5   swap       
/dev/sdb6        689657219656EED6                       ntfs       HDDRECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c44f2607-cfcd-4518-bcdd-2879d5f831fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=c44f2607-cfcd-4518-bcdd-2879d5f831fb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c44f2607-cfcd-4518-bcdd-2879d5f831fb ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c44f2607-cfcd-4518-bcdd-2879d5f831fb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set c44f2607-cfcd-4518-bcdd-2879d5f831fb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 40100ABC100AB944
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 845A30F65A30E718
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 689657219656EED6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=c44f2607-cfcd-4518-bcdd-2879d5f831fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4b458626-0b3c-4371-abae-7875c6a230e5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 316.409221649 = 339.741814784  boot/grub/grub.cfg                             1
 235.097656250 = 252.434186240  boot/initrd.img-2.6.35-22-generic              2
 235.282348633 = 252.632498176  boot/initrd.img-2.6.35-28-generic              2
 350.429588318 = 376.270905344  boot/vmlinuz-2.6.35-22-generic                 1
 350.468845367 = 376.313057280  boot/vmlinuz-2.6.35-28-generic                 1
 235.282348633 = 252.632498176  initrd.img                                     2
 235.097656250 = 252.434186240  initrd.img.old                                 2
 350.468845367 = 376.313057280  vmlinuz                                        1
 350.429588318 = 376.270905344  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff ad 04  00 00 f0 8f 1e 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff ac 94  1e 01 01 00 70 01 00 00  |............p...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sda 


```

---

### Post by Rubi1200 on 2011-06-24
neo1786,
at this point there does not appear to be an awful lot to recover I am sorry to say :(

You can try using Testdisk again and run the Deeper Search function and/or use Photorec to at least try and recover some of your data (I sincerely hope you have backups of important data).

Failing that, you may be left with little choice but to reinstall everything from scratch.

---

### Post by Quackers on 2011-06-24
It seems that the extended partition extends beyond the end of the disc. This can happen sometimes with testdisk and I would normally advise that it be fixed.
However, in your case it seems that the data you want to recover appears to be lost (unless it's on a Linux partition). Can you view the NTFS partition in the Places menu in the Ubuntu live cd? If so, grab what you can, then re-install.

---

### Post by neo1786 on 2011-06-24
thanks guys, most of the data had been backed up, but not all of it. is there any way i can run the windows recovery?? i use windows for microsoft office and since the laptop shipped with windows, i think tht running recovery shud re install windows.....im just guessing tho...do u guys know if tht is possible here?

---

### Post by neo1786 on 2011-06-24
> **Rubi1200 said:**
> neo1786,
at this point there does not appear to be an awful lot to recover I am sorry to say :(

You can try using Testdisk again and run the Deeper Search function and/or use Photorec to at least try and recover some of your data (I sincerely hope you have backups of important data).

Failing that, you may be left with little choice but to reinstall everything from scratch.

ALrite looks like ill have to do a fresh install afterall!

---

### Post by Quackers on 2011-06-24
There doesn't appear to be a Windows recovery partition visible (unless that's the last partition shown there).
Did you make a set of recovery dvd's? Always advisable in my experience.

---

### Post by oldfred on 2011-06-24
Windows does not normally boot from logical partitions. The grub menu entry for Vista (Probably your recovery) in sdb3 has the same UUID as the current sda6. It might boot since UUIDs are same. But partition boot sector proably does not match current location. I know you can use testdisk to repair a NTFS boot sector to get XP to boot in a logical partition, but do not think Vista or 7 work.

Otherwise you might be able to convert it to a primary partition, but you have to delete another primary to have one available. It is not impossible and has some risks, but might be doable if you are desperate. Then you may be able to repair partition boot sector and get it to boot.

---

### Post by neo1786 on 2011-06-24
```

/media/HDDRECOVERY$ ls
BIN      DATA.INI     PLANDATA.INI  System Volume Information
BOOT     EDITAF.BAT   PLANFOLDER    !V6_00_03.VRP
BOOTMGR  IMAGES_BOOT  SOURCES       ZZIMAGES

```

This is sdb6 the recovery...is it possible?

---

### Post by neo1786 on 2011-06-24
> **Quackers said:**
> There doesn't appear to be a Windows recovery partition visible (unless that's the last partition shown there).
Did you make a set of recovery dvd's? Always advisable in my experience.

yes the last one is the recovery..i didnt make any DVD's :(
will remember from here on

---

