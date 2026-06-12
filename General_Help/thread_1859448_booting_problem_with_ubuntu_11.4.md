---
title: "booting problem with ubuntu 11.4?"
date: 2011-10-13
forum: General Help
---

### Post by geekhush on 2011-10-13
Hi all, I am a newbie t linux and using ubuntu 11.4 on a dualboot machine running windows 7 alongside, so i migrated from a wubi installation to a native install some time ago. and whats bugging me is this problem with ubuntu where i am not able to boot into ubuntu normally. ten tries and BOOM! success. But when i boot windows 7 it just runs fine. and then every thing on ubuntu runs late. Not that i did not have this problem when i was using wubi but i fixed it using the guide provided by BCBC. so if anybody out there can help me please do. i have been trying to google this issue since ages and yet i couldn't get a clue. heres the boot info script.
                  ```

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 871909375 
                       sectors, but according to the info from fdisk, it has 
                       1984 sectors.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 871911424. But according to the info from 
                       fdisk, sda2 starts at sector 2048. According to the 
                       info in the boot sector, sda2 has 104857599 sectors, 
                       but according to the info from fdisk, it has 871909375 
                       sectors.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048   871,911,423   871,909,376  42 SFS
/dev/sda3         871,911,424   976,771,119   104,859,696  42 SFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   163,840,319   163,840,257   7 NTFS / exFAT / HPFS
/dev/sdb2         163,840,381   625,121,279   461,280,899   f W95 Extended (LBA)
/dev/sdb5         163,842,048   327,677,951   163,835,904   7 NTFS / exFAT / HPFS
/dev/sdb6         327,680,703   491,520,942   163,840,240   7 NTFS / exFAT / HPFS
/dev/sdb7         491,521,023   625,121,279   133,600,257   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7C18DA6618DA1F48                       ntfs       Movies
/dev/sda2        C44EDDD04EDDBB7E                       ntfs       Gen
/dev/sdb1        7C8453138452CF70                       ntfs       Wild
/dev/sdb6        7C3CD30D3CD2C0F6                       ntfs       Songs
/dev/sdb7        4d3caac4-393c-4825-b2e5-f17fe1f63a14   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /media/Songs             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb7/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=4d3caac4-393c-4825-b2e5-f17fe1f63a14 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=4d3caac4-393c-4825-b2e5-f17fe1f63a14 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4d3caac4-393c-4825-b2e5-f17fe1f63a14 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4d3caac4-393c-4825-b2e5-f17fe1f63a14 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 4d3caac4-393c-4825-b2e5-f17fe1f63a14
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 7C8453138452CF70
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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# root was on /dev/sdb7 when migrated
UUID=4d3caac4-393c-4825-b2e5-f17fe1f63a14    /    ext4    errors=remount-ro    0    1
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 286.563853741 = 307.695595008  boot/grub/core.img                             1
 276.516215801 = 296.907025920  boot/grub/grub.cfg                             1
 234.516112804 = 251.809758720  boot/initrd.img-2.6.35-22-generic              2
 247.234862804 = 265.466412544  boot/initrd.img-2.6.38-11-generic              2
 286.510173321 = 307.637956096  boot/vmlinuz-2.6.35-22-generic                 1
 286.514388561 = 307.642482176  boot/vmlinuz-2.6.38-11-generic                 1
 247.234862804 = 265.466412544  initrd.img                                     2
 234.516112804 = 251.809758720  initrd.img.old                                 2
 286.514388561 = 307.642482176  vmlinuz                                        1
 286.510173321 = 307.637956096  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  df a6 5a 0c 00 00 00 00  |FILE0.....Z.....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  0a 00 00 00 00 00 00 00  |................|
00000030  9f 6a 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |.j..........`...|
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
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 9f 6a  |...............j|
00000200
Unknown BootLoader on sda3


Unknown BootLoader on sdb2

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

Unknown BootLoader on sdb5

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


=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
```

---

### Post by bcbc on 2011-10-13
There are a few things here, not sure if they are the cause of the problem:
1. /dev/sda has windows' proprietary dynamic 'disks' - so you shouldn't mount this as you are in /etc/fstab (I believe this could result in potential data loss since linux doesn't understand dynamic disks (although I can't say for sure what will happen e.g. if you are just reading data off it - but writing would almost certainly be a risk).

2. /dev/sdb5 isn't recognized - not sure what that is.

3. /dev/sdb7 is type '7' NTFS. 
> /dev/sdb7         491,521,023   625,121,279   133,600,257   [COLOR=Red]7[/COLOR] NTFS / exFAT / HPFS

/dev/sdb7        4d3caac4-393c-4825-b2e5-f17fe1f63a14   [COLOR=Red]ext4[/COLOR] 
This isn't a big deal - the old migration script (2.0) was quite happy to migrate to an NTFS partition and convert the file system to ext4 (no known issues with this). However, it's not a good practice and I've prevented this in the latest 2.1 script. You should modify this using sfdisk or some other disk utility. (I'd advise backing up before using sfdisk as a precaution) - the following should do it (refer to 'man sfdisk' for more info) Note the "7" in the command is the partition number:
```
sudo sfdisk --change-id /dev/sdb 7 83
```As I said, I don't know if any of this is causing the strange boot issues. I get a bit nervous with the dynamic disks because basically linux and windows are mounting the drive and using it (potentially) with a completely different idea about what constitutes a partition.

---

### Post by oldfred on 2011-10-13
Just like Ubuntu automatically runs fsck on every 40 or so reboots, you should run chkdsk on your NTFS partitions. My old XP partition was slow mounting and booting. After chkdsk both improved. Using a Windows 7 repair USB to run chkdsk was better than the XP chkdsk also.

Not sure if chkdsk even works on the dynamic partitions. Some Windows tools do not work with Windows own dynamic partitions. 

There are ways to convert back but they are somewhat risky. Microsoft's official policy is to backup & delete everything and create new basic partitions.

---

### Post by bcbc on 2011-10-14
PS Please also post your full computer specs. Might be something causing intermittent issues there as well.

Thanks

---

### Post by geekhush on 2011-10-14
Hi guys, thanks a lot for ya time.Heres my computer spec,
```
H/W path    Device     Class          Description
=================================================
                       system         Desktop Computer
/0                     bus            C51PVGM-M
/0/0                   memory         128KiB BIOS
/0/6                   processor      AMD Sempron(tm) Processor LE-1250
/0/6/c                 memory         128KiB L1 cache
/0/6/d                 memory         512KiB L2 cache
/0/1d                  memory         4GiB System Memory
/0/1d/0                memory         2GiB DIMM
/0/1d/1                memory         2GiB DIMM
/0/1d/2                memory         DIMM [empty]
/0/1d/3                memory         DIMM [empty]
/0/1                   memory         RAM memory
/0/0.1                 memory         RAM memory
/0/0.2                 memory         RAM memory
/0/0.3                 memory         RAM memory
/0/0.4                 memory         RAM memory
/0/0.5                 memory         RAM memory
/0/0.6                 memory         RAM memory
/0/0.7                 memory         RAM memory
/0/2                   bridge         C51 PCI Express Bridge
/0/3                   bridge         C51 PCI Express Bridge
/0/4                   bridge         C51 PCI Express Bridge
/0/5                   display        C51 [GeForce 6150 LE]
/0/9                   memory         RAM memory
/0/a                   bridge         MCP51 LPC Bridge
/0/a.1                 bus            MCP51 SMBus
/0/a.2                 memory         RAM memory
/0/b                   bus            MCP51 USB Controller
/0/b.1                 bus            MCP51 USB Controller
/0/d                   storage        MCP51 IDE
/0/e        scsi2      storage        MCP51 Serial ATA Controller
/0/e/0      /dev/sda   disk           500GB ST3500413AS
/0/e/0/1               volume         992KiB SFS partition
/0/e/0/2               volume         415GiB Windows NTFS volume
/0/e/0/3               volume         50GiB Windows NTFS volume
/0/e/1      /dev/sdb   disk           320GB WDC WD3200AAJS-6
/0/e/1/1    /dev/sdb1  volume         78GiB Windows NTFS volume
/0/e/1/2    /dev/sdb2  volume         219GiB Extended partition
/0/e/1/2/5  /dev/sdb5  volume         78GiB HPFS/NTFS partition
/0/e/1/2/6  /dev/sdb6  volume         78GiB HPFS/NTFS partition
/0/e/1/2/7  /dev/sdb7  volume         63GiB HPFS/NTFS partition
/0/10                  bridge         MCP51 PCI Bridge
/0/10/6                bus            VT82xxxxx UHCI USB 1.1 Controller
/0/10/6.1              bus            VT82xxxxx UHCI USB 1.1 Controller
/0/10/6.2              bus            USB 2.0
/0/10/7                communication  SoftV92 SpeakerPhone SoftRing Modem with S
/0/10/9     eth1       network        RTL-8139/8139C/8139C+
/0/10.1                multimedia     MCP51 High Definition Audio
/0/14                  bridge         MCP51 Ethernet Controller
/0/100                 bridge         K8 [Athlon64/Opteron] HyperTransport Techn
/0/101                 bridge         K8 [Athlon64/Opteron] Address Map
/0/102                 bridge         K8 [Athlon64/Opteron] DRAM Controller
/0/103                 bridge         K8 [Athlon64/Opteron] Miscellaneous Contro

```

also guys my pc has become super slow, though i ve got 4gb ram as u can see..please do suggest something on this too
P.S-- Thanks for guiding me BCBC, u v been helping me for like more than a month now. So u really deserve at-least a JUMBO thanks :)

---

### Post by bcbc on 2011-10-14
I can't see anything specifically on the spec. Is this a custom build or do you have a brand/model number?

But I suspect this is not the problem. Maybe there is a component failing. Just because of the intermittent nature of it - the file system corruption and the facts that it's slowing down.

Try running the chkdsk that oldfred suggested. 
Maybe if you have an OEM tool that will do a hardware check, run that. It should point out any failing component.

---

### Post by geekhush on 2011-10-14
hi, well mine's is a custom build one, and ya about the hardware failure thing i think, it MAY BE the problem. yu may see it here, i posted it on the windows forum [http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/2e812cf5-9dc7-4c08-8d7f-dd206b62c74e/#58072cd2-2344-4f60-a527-6f7ac739b283](http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/2e812cf5-9dc7-4c08-8d7f-dd206b62c74e/#58072cd2-2344-4f60-a527-6f7ac739b283) but like since i don't 've much idea about it still i dont think this might be the cause, yet my windows too is slowing down, and about the OEM tool could u kindly suggest me one.and also "/dev/sdb5 isn't recognized " thats a bitlocker encrypted drive which wont unlock even if i provide the correct password and has got my 40 gb of imp data ](*,)  (i am really a sad soul, m i not) LOL
and in case this could provide more clue heres the detailed system spec.
```
ubuntu
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: C51PVGM-M
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 10/15/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor LE-1250
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 6
          bus info: cpu@0
          version: 15.15.2
          slot: Socket AM2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 2GiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:c000(size=4096) memory:fd700000-fd7fffff ioport:fde00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:b000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:9000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:16 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:c0000000-c001ffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f400(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi2
          logical name: scsi3
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
        *-disk:0
             description: ATA Disk
             product: ST3500413AS
             vendor: Seagate
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: JC45
             serial: Z2A1W52B
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=36ba5f49
           *-volume:0 UNCLAIMED
                description: SFS partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                capacity: 992KiB
                capabilities: primary
           *-volume:1 UNCLAIMED
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@2:0.0.0,2
                version: 3.1
                serial: a6c6c899-1865-a346-b990-4e42cce7e004
                size: 415GiB
                capacity: 415GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2003-01-01 00:17:15 filesystem=ntfs label=Movies state=clean
           *-volume:2 UNCLAIMED
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@2:0.0.0,3
                version: 3.1
                serial: 08a596d3-b135-ef47-b164-509dee05be09
                size: 49GiB
                capacity: 50GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-08-25 09:19:55 filesystem=ntfs label=Gen state=clean
        *-disk:1
             description: ATA Disk
             product: WDC WD3200AAJS-6
             vendor: Western Digital
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 01.0
             serial: WD-WCAT15949426
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00000001
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: 1e6e6e94-a218-1d47-8add-ee6426f70128
                size: 78GiB
                capacity: 78GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-07-30 16:27:45 filesystem=ntfs label=Wild state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdb2
                size: 219GiB
                capacity: 219GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 78GiB
              *-logicalvolume:1
                   description: HPFS/NTFS partition
                   physical id: 6
                   logical name: /dev/sdb6
                   logical name: /media/Songs
                   capacity: 78GiB
                   configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-logicalvolume:2
                   description: HPFS/NTFS partition
                   physical id: 7
                   logical name: /dev/sdb7
                   logical name: /
                   capacity: 63GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:a000(size=4096) memory:fdb00000-fdbfffff memory:fda00000-fdafffff
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 6
             bus info: pci@0000:04:06.0
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:16 ioport:ac00(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 6.1
             bus info: pci@0000:04:06.1
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:17 ioport:a800(size=32)
        *-usb:2
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 6.2
             bus info: pci@0000:04:06.2
             version: 65
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:18 memory:fdbff000-fdbff0ff
        *-communication UNCLAIMED
             description: Communication controller
             product: SoftV92 SpeakerPhone SoftRing Modem with SmartSP
             vendor: Conexant Systems, Inc.
             physical id: 7
             bus info: pci@0000:04:07.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fdbe0000-fdbeffff ioport:a400(size=8)
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 9
             bus info: pci@0000:04:09.0
             logical name: eth1
             version: 10
             serial: 00:1b:b9:e1:98:53
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:19 ioport:a000(size=256) memory:fdbfe000-fdbfe0ff
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fe028000-fe02bfff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 04:4b:80:80:80:03
          size: 10000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=half latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=10Mbit/s
          resources: irq:20 memory:fe02c000-fe02cfff ioport:dc00(size=8)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
```

---

### Post by oldfred on 2011-10-14
Also how full is NTFS partition. They work best with 30% free and start to slow system down with 20% free.

---

### Post by bcbc on 2011-10-14
OEM = original equipment manufacturer who'll often supply tools to help diagnose issues. So this won't apply on a custom build.

So you'll have to rely on 3rd party tools. The 'disk utility' should report errors on the drive if it is [SMART]("http://en.wikipedia.org/wiki/S.M.A.R.T.") enabled. You should also be able to do a memory check for RAM exceptions at startup or from a live cd's extended menu.

---

### Post by geekhush on 2011-10-15
Ok so i did a chkdsk scan on windows..yet no improvement, and i checked for errors too using this software called tuneup utility, and nothing helps.. please somebody sugest me something i am really in need of help :(

---

### Post by oldfred on 2011-10-15
There are some BIOS settings that may make a difference. Do you have fastboot or quickboot turned on? some other settings also may make a difference. check AHCI, mode large, auto, IDE. Large or LBA is usually best.

---

