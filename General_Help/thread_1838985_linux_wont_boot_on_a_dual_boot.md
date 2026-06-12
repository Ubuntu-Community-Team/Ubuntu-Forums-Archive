---
title: "linux wont boot on a dual boot ?"
date: 2011-09-04
forum: General Help
---

### Post by geekhush on 2011-09-04
hi, i am new to linux and i wanna explore it, so i recently installed ubuntu 10.10 32 bits via wubi on windows 7 (tried on both 32 and 64 bits)...now the problem is i can't boot into linux most of the time, i also tried with kubuntu 10.10, and lubuntu 10.10. and also i migrated the wubi installation (ubuntu 10.10) to a full installation. But the problem remains ... not that i cant boot into linux at all but..its like out of 10 tries i can successfully boot only about 2-3 times ... its the same with all destros i tried :\... :confused: 
any help really appreciated  :-({|=
 thanks

---

### Post by raja.genupula on 2011-09-04
Hi
my guess is , it seems that problem with your system not nay other issue(as the way you mentioned here) . but give a try give us the output of ```
dmesg >> out.txt
``` in terminal in next boot up . attach here .

---

### Post by Rubi1200 on 2011-09-05
Hi and welcome to the forums geekhush :)

To give us a better overview, please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by geekhush on 2011-09-05
hi, thanks for the reply :) 
i did as u suggested me and ve uploaded a file .gz in here( the out.txt file) .... please do help me :)
 and [Boot info script]("http://bootinfoscript.sourceforge.net/") is attached as RESULTS.txt.tar.gz .... thanks for ua time :)

---

### Post by Rubi1200 on 2011-09-07
For those concerned:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 80. But according to the info from fdisk, 
                       sda7 starts at sector 491521023.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sdb1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sdb1 has 871909375 
                       sectors, but according to the info from fdisk, it has 
                       1984 sectors.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb2 starts 
                       at sector 871911424. But according to the info from 
                       fdisk, sdb2 starts at sector 2048. According to the 
                       info in the boot sector, sdb2 has 104857599 sectors, 
                       but according to the info from fdisk, it has 871909375 
                       sectors.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   163,840,319   163,840,257   7 NTFS / exFAT / HPFS
/dev/sda2         163,840,381   625,121,279   461,280,899   f W95 Extended (LBA)
/dev/sda5         163,842,048   327,677,951   163,835,904   7 NTFS / exFAT / HPFS
/dev/sda6         327,680,703   491,520,942   163,840,240   7 NTFS / exFAT / HPFS
/dev/sda7         491,521,023   625,121,279   133,600,257   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63         2,047         1,985  42 SFS
/dev/sdb2    *          2,048   871,911,423   871,909,376  42 SFS
/dev/sdb3         871,911,424   976,771,119   104,859,696  42 SFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 129     3,907,007     3,906,879   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       0199557a-550c-42a4-806c-f70835ddeef1   ext4       
/dev/sda1        7C8453138452CF70                       ntfs       wild
/dev/sda6        7C3CD30D3CD2C0F6                       ntfs       Songs
/dev/sda7        3604FEA904FE6B6F                       ntfs       GaMeZ
/dev/sdb1        7C18DA6618DA1F48                       ntfs       movies
/dev/sdb2        C44EDDD04EDDBB7E                       ntfs       Ubuntu
/dev/sdc1        700B-04EF                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdc1        /media/700B-04EF         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


======================== sda1/Wubi/boot/grub/grub.cfg: =========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7c8453138452cf70
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7c8453138452cf70
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7c8453138452cf70
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

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  12.481174469 = 13.401559040   boot/grub/grub.cfg                             1
   1.455726624 = 1.563074560    boot/initrd.img-2.6.35-22-generic              2
  10.191497803 = 10.943037440   boot/vmlinuz-2.6.35-22-generic                 1
   1.455726624 = 1.563074560    initrd.img                                     2
  10.191497803 = 10.943037440   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  c7 5c 36 69 5e d3 d2 42  fd f2 fb af bf 01 b7 c4  |.\6i^..B........|
00000010  0b 29 a4 94 fa d2 71 bc  28 4c 28 45 ff 5e f2 ea  |.)....q.(L(E.^..|
00000020  bf 08 39 a3 85 c1 1b 29  74 d0 c3 0d 83 b4 31 44  |..9....)t.....1D|
00000030  23 09 ac 31 41 02 29 ec  8b 2f c5 25 8c 52 49 fe  |#..1A.)../.%.RI.|
00000040  02 5c 51 23 0c 0b fc ff  f2 ca 30 73 74 8b 33 b8  |.\Q#......0st.3.|
00000050  f0 22 32 4c a6 98 62 f2  c2 06 31 0a 72 cc bd b8  |."2L..b...1.r...|
00000060  c2 e6 48 26 8d a4 4f b1  45 5b 1c 33 d3 30 17 d4  |..H&..O.E[.3.0..|
00000070  c8 2d 0a 6b 63 dc 33 31  45 c3 73 af 17 67 bb 35  |.-.kc.31E.s..g.5|
00000080  9d 15 b9 e2 28 cc 4b 9c  82 0d 2f ae 4c 5d 72 d5  |....(.K.../.L]r.|
00000090  c5 f9 b2 b0 c6 4d 83 f4  d0 c6 85 2e d3 4a 36 00  |.....M.......J6.|
000000a0  34 97 e6 9a 6e cb ac b7  db 05 fd 7c 92 ca 28 7b  |4...n......|..({|
000000b0  94 72 42 84 07 9c b2 e1  19 c1 cd 71 dc a6 46 ac  |.rB........q..F.|
000000c0  f1 40 2d 2f 04 30 e2 06  b1 74 0b d4 8c 27 f4 37  |.@-/.0...t...'.7|
000000d0  c0 45 1b 6d 38 df 93 3f  3d ba d6 82 df a2 05 4a  |.E.m8..?=......J|
000000e0  9a ab ae f9 e2 46 17 64  1f 03 f2 78 ee 38 9b b4  |.....F.d...x.8..|
000000f0  63 23 50 e8 0c a5 ba 37  ef b9 f7 fe fb e0 98 00  |c#P....7........|
00000100  2c 79 e1 85 83 4e 90 f0  7d b7 8d cd 35 73 d7 7d  |,y...N..}...5s.}|
00000110  b7 9a 02 db cd 03 0f 3a  50 7f bd 0c d7 6b bf 7d  |.......:P....k.}|
00000120  f5 3a 70 83 0e f8 e1 8b  0f 7e 3b e8 c0 33 cf f8  |.:p......~;..3..|
00000130  e9 a7 3f 8f 00 e5 a3 d3  8e 3c fc 88 9f 07 0e 38  |..?......<.....8|
00000140  70 7f 3d 0e 3b a0 63 ff  b7 cb 82 b7 44 91 e8 56  |p.=.;.c.....D..V|
00000150  37 b3 4b 68 61 14 4a 23  54 af de e6 10 8f f8 ce  |7.Kha.J#T.......|
00000160  74 04 b9 04 c3 b0 d1 0b  a8 95 ae 76 b7 e8 05 c4  |t..........v....|
00000170  3e 66 90 a1 39 4d 81 a1  c0 06 f1 de c6 90 cc 19  |>f..9M..........|
00000180  a4 54 ab 3b a1 08 4f b8  38 5e b0 83 00 f5 18 07  |.T.;..O.8^......|
00000190  f3 4c a5 b0 8c b0 63 3d  0c 20 00 39 1a 48 c1 06  |.L....c=. .9.H..|
000001a0  02 af 87 cb 9a 9a 36 8e  13 44 92 11 b1 64 d1 d8  |......6..D...d..|
000001b0  19 c9 a6 96 36 93 69 23  13 54 33 8e c2 08 00 ef  |....6.i#.T3.....|
000001c0  ff ff 07 ef ff ff 83 06  00 00 00 f0 c3 09 00 ef  |................|
000001d0  ff ff 05 ef ff ff 83 f6  c3 09 af 0b c4 09 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5

00000000  eb 58 90 2d 46 56 45 2d  46 53 2d 00 02 08 00 00  |.X.-FVE-FS-.....|
00000010  00 00 00 00 00 f8 00 00  3f 00 f0 00 83 06 00 00  |........?.......|
00000020  00 00 00 00 e0 1f 00 00  00 00 00 00 00 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 00 00 00 00 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  a0 fb 7d b4 7d 8b f0 ac  |{......|..}.}...|
00000070  98 40 74 0c 48 74 0e b4  0e bb 07 00 cd 10 eb ef  |.@t.Ht..........|
00000080  a0 fd 7d eb e6 cd 16 cd  19 00 00 00 00 00 00 00  |..}.............|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  3b d6 67 49 29 2e d8 4a  83 99 f6 a3 39 e3 d0 01  |;.gI)..J....9...|
000000b0  00 00 fc c0 00 00 00 00  00 00 fd c0 00 00 00 00  |................|
000000c0  00 00 fe c0 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000190  00 00 00 00 00 00 00 00  78 78 78 78 78 78 78 78  |........xxxxxxxx|
000001a0  78 78 78 78 78 78 78 78  78 78 78 78 78 78 78 78  |xxxxxxxxxxxxxxxx|
*
000001e0  78 78 78 78 78 78 78 78  ff ff ff ff ff ff ff ff  |xxxxxxxx........|
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200

MFT Sector of sdb1

00000000  46 49 4c 45 30 00 03 00  df a6 5a 0c 00 00 00 00  |FILE0.....Z.....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  0a 00 00 00 00 00 00 00  |................|
00000030  9e 6a 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |.j..........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 80 3d 04 00 00 00 00  |..........=.....|
000000e0  00 80 3d 04 00 00 00 00  06 00 00 00 00 00 00 00  |..=.............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  d7 43 00 00 00 00 00 00  |.........C......|
00000120  40 00 00 00 00 00 00 00  00 80 3d 04 00 00 00 00  |@.........=.....|
00000130  00 80 3d 04 00 00 00 00  00 80 3d 04 00 00 00 00  |..=.......=.....|
00000140  32 d8 43 00 00 0c 00 c1  b0 00 00 00 50 00 00 00  |2.C.........P...|
00000150  01 00 40 00 00 00 09 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  02 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 30 00 00 00 00 00 00  f0 21 00 00 00 00 00 00  |.0.......!......|
00000180  f0 21 00 00 00 00 00 00  31 01 ff ff 0b 31 02 be  |.!......1....1..|
00000190  0e f4 00 00 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 9e 6a  |...............j|
00000200
Unknown BootLoader on sdb3


Unknown BootLoader on sdc1

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 40 01 00  |.<.MSDOS5.0..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 40 00 81 00 00 00  |........?.@.....|
00000020  3f 9d 3b 00 80 01 29 ef  04 0b 70 4e 4f 20 4e 41  |?.;...)...pNO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 53 79 73  |..'..Invalid Sys|
00000190  74 65 6d 20 44 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem Disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 50  72 65 73 73 20 41 6e 79  |d then Press Any|
000001d0  20 4b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | Key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory


```

---

### Post by geekhush on 2011-09-07
hi, now it seems that the above problem is solved, but i am not very sure since it has worked well for 3 days now ( after posting this) and just yesterday i upgraded to ubuntu 11.4. but now what is bothering me is the blank desktop and i cant see anything when i enlarge a window....i see things only when the window is small... but the side bar and the panel, i can see them... does anyone has a clue as to why it's happening.?  every time i wanna explore linux something happens :( any help really really appreciated.

thanks :)

---

### Post by Rubi1200 on 2011-09-08
I suggest you refer to the Wubi Megathread which contains information on common problems with Wubi installs:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

The following blog by forum member bcbc also has a ton of useful information:
[http://ubuntu-with-wubi.blogspot.com/](http://ubuntu-with-wubi.blogspot.com/)

---

### Post by geekhush on 2011-09-17
hi, thanks a LOT! the thread has all the problms and thir solution listd :) thanks a lot :D

---

### Post by Rubi1200 on 2011-09-18
No problem, you are more than welcome :-)

---

