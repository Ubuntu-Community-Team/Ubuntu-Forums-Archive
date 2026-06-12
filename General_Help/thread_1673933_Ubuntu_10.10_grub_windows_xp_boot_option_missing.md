---
title: "Ubuntu 10.10 grub windows xp boot option missing"
date: 2011-01-23
forum: General Help
---

### Post by bear_jacobsen on 2011-01-23
I recently installed Ubuntu 10.10 on my desktop which also have windows xp installed. After the installation I could boot to both Ubuntu and Windows. I then installed some updates from the update manager in Ubuntu 10.10 and after this the windows option in the grub boot menu is gone.

I am newbie so I don't know what is wrong and I am hoping someone can help with this issue,

The boot_info_script055.sh returned the following result

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   110,782,406   110,702,082   7 HPFS/NTFS
/dev/sda3         146,496,735   156,232,124     9,735,390  db CP/M / CTOS / ...
/dev/sda4         110,782,462   146,495,487    35,713,026   5 Extended
/dev/sda5         110,782,464   144,910,335    34,127,872  83 Linux
/dev/sda6         144,912,384   146,495,487     1,583,104  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdb2         204,796,620   318,119,129   113,322,510   7 HPFS/NTFS
/dev/sdb3         318,119,191   976,768,064   658,648,874   5 Extended
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D6-0301                              vfat       DellUtility                   
/dev/sda2        1CD4CD19D4CCF5D4                       ntfs                                     
/dev/sda3                                               vfat       DellRestore                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        254411b9-7805-450c-8673-8b30ce0d50ff   ext4                                     
/dev/sda6        ecf9a2be-2f40-442e-bd6f-02899983ecd6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A2C274FCC274D64F                       ntfs       Data                          
/dev/sdb2        4496DFA196DF91B2                       ntfs       Media                         
/dev/sdb3: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=254411b9-7805-450c-8673-8b30ce0d50ff ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=254411b9-7805-450c-8673-8b30ce0d50ff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=254411b9-7805-450c-8673-8b30ce0d50ff ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=254411b9-7805-450c-8673-8b30ce0d50ff ro single 
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
    search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 254411b9-7805-450c-8673-8b30ce0d50ff
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=254411b9-7805-450c-8673-8b30ce0d50ff /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ecf9a2be-2f40-442e-bd6f-02899983ecd6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  61.3GB: boot/grub/core.img
  67.9GB: boot/grub/grub.cfg
  58.3GB: boot/initrd.img-2.6.35-22-generic
  58.4GB: boot/initrd.img-2.6.35-24-generic
  61.4GB: boot/vmlinuz-2.6.35-22-generic
  61.4GB: boot/vmlinuz-2.6.35-24-generic
  58.4GB: initrd.img
  58.3GB: initrd.img.old
  61.4GB: vmlinuz
  61.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  87 a9 e6 d4 e5 ef 14 e1  f5 84 2f db 38 f8 2d 88  |........../.8.-.|
00000010  57 dc 19 1c 32 3a 65 a5  2b 5b 3a 83 a4 4b b0 e3  |W...2:e.+[:..K..|
00000020  78 aa 9f 6c a9 f4 d2 f8  41 55 f6 a8 8a 61 71 cf  |x..l....AU...aq.|
00000030  10 85 1e 27 cd ea 8d 94  d9 d7 8e 6b f9 65 84 ed  |...'.......k.e..|
00000040  a3 98 3f ea 65 5f 63 3d  80 8b f5 1f fa 9e a3 34  |..?.e_c=.......4|
00000050  a2 e3 c5 e3 ec 4a 99 5d  10 7e c5 6b 51 e7 27 b9  |.....J.].~.kQ.'.|
00000060  4d e0 88 13 92 1e 89 6c  6a d5 35 fb 6a b6 96 55  |M......lj.5.j..U|
00000070  3c f5 a4 bc 3a 65 30 93  4b db f3 05 e3 c6 aa 93  |<...:e0.K.......|
00000080  5b f5 8d 02 59 b5 4d 88  8e 42 26 d0 11 cb 9b 4e  |[...Y.M..B&....N|
00000090  aa 62 a5 1d bb 96 f5 17  20 ae 1b 62 d2 ed 55 eb  |.b...... ..b..U.|
000000a0  33 e3 85 12 9a a7 a7 e0  a5 4a c0 fe 0e 9a 4c d1  |3........J....L.|
000000b0  61 6c f4 0e d4 f2 89 d6  4a 0d 55 a6 4b ff 02 a9  |al......J.U.K...|
000000c0  a6 f9 6c 52 a5 bc 17 13  48 c3 77 86 86 f0 8b 2d  |..lR....H.w....-|
000000d0  c3 48 dc fa 23 fd 69 52  45 2a a3 19 d5 fb fd dc  |.H..#.iRE*......|
000000e0  75 fa 83 28 48 df db 19  4a 9d 9f a8 83 24 27 69  |u..(H...J....$'i|
000000f0  ad 99 77 fc 63 14 9b 5d  f9 bf 32 d8 17 ef 0a 48  |..w.c..]..2....H|
00000100  24 17 94 bd a9 6b 6a 0e  3f 1f c5 20 dd 4b 46 19  |$....kj.?.. .KF.|
00000110  ec f4 17 a9 a7 9c 06 03  29 51 68 30 23 67 f6 d1  |........)Qh0#g..|
00000120  97 23 e9 2f 8b 66 4b 79  09 0f 57 f7 3d 79 25 e4  |.#./.fKy..W.=y%.|
00000130  26 f2 c4 61 24 58 94 62  75 f8 66 07 ea da 6a 70  |&..a$X.bu.f...jp|
00000140  a5 4e b9 d0 f3 18 54 0c  18 4c 31 2d 4d 5d 42 12  |.N....T..L1-M]B.|
00000150  52 3d ed 9c b6 f2 47 5e  3d 94 0e 79 d2 d1 81 f7  |R=....G^=..y....|
00000160  ea fb 58 49 9e bc 25 47  68 63 5e f2 cf 2a ff c1  |..XI..%Ghc^..*..|
00000170  e3 3f f7 66 de 0b a3 b1  66 fd 46 ed 84 b1 f6 de  |.?.f....f.F.....|
00000180  7a 5a a7 b8 1a 48 88 9a  1e c6 10 68 de 0f 0b 40  |zZ...H.....h...@|
00000190  df 44 4b 9c 44 69 71 70  d3 28 c6 ef 9b 52 b6 2e  |.DK.Diqp.(...R..|
000001a0  13 0a c0 e0 93 04 b5 5f  f9 67 94 4f a8 2a 8b 22  |......._.g.O.*."|
000001b0  42 e2 ab 0d 94 73 0d 11  3d 9c bc 34 72 4b 00 fe  |B....s..=..4rK..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 08 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c0  08 02 00 30 18 00 00 00  |...........0....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb3

00000000  ce 15 77 32 1e de a5 f6  4e df 83 ad 6e 5c 3d b7  |..w2....N...n\=.|
00000010  d3 9b c5 a9 ae 55 03 4d  e8 1d 09 bb 1b cd de 80  |.....U.M........|
00000020  28 c4 6f 5e 24 d1 02 85  d0 23 87 ef 86 5a de 7f  |(.o^$....#...Z..|
00000030  04 d2 9b d2 ec b8 5b 57  7f 7b 3d fa f3 22 fc ad  |......[W.{=.."..|
00000040  0e 27 bc b0 b6 fe 07 80  18 7f c5 7f c0 1f 71 1d  |.'............q.|
00000050  4b 15 99 c3 c2 64 6f f4  49 cf 6f e7 7b a3 df b7  |K....do.I.o.{...|
00000060  d5 bf 9d c0 80 07 fd e8  01 c9 15 ca 51 02 53 06  |............Q.S.|
00000070  2a 9e df 92 fc e6 3c 55  80 44 59 43 60 c6 d5 d5  |*.....<U.DYC`...|
00000080  28 4b 54 ff 17 cc 8c 64  8c c6 96 73 13 52 9c df  |(KT....d...s.R..|
00000090  d0 25 37 cb 96 d5 9b 45  8b e3 e3 a7 8b e6 a3 b8  |.%7....E........|
000000a0  cb ba 14 df e8 b0 01 78  bc 00 72 00 e7 e4 4e 1d  |.......x..r...N.|
000000b0  ce 9b 02 1b f8 e6 08 1f  91 db f8 00 30 23 f9 54  |............0#.T|
000000c0  bb 5d 85 06 d6 fe ea 75  48 26 d8 55 91 1b f1 c0  |.].....uH&.U....|
000000d0  07 13 32 57 d3 f6 99 02  06 b7 b9 d9 65 05 b7 ed  |..2W........e...|
000000e0  09 d7 05 db 4e 39 bc 60  8f 6d 13 14 b9 8a 42 6e  |....N9.`.m....Bn|
000000f0  77 b7 17 ca f9 95 4d 6f  92 70 2f 8c b9 92 44 33  |w.....Mo.p/...D3|
00000100  d5 bf 3a 90 f4 2a 6a d4  a3 db d1 90 7b 7f 46 7f  |..:..*j.....{.F.|
00000110  d0 cc 8a 3d bf 3b 00 3c  00 75 39 14 98 85 55 ad  |...=.;.<.u9...U.|
00000120  f6 9e c4 c2 0e 29 49 85  b7 04 88 45 13 c7 1b 8e  |.....)I....E....|
00000130  d4 34 b6 e1 b0 3a a4 93  5b 18 92 96 73 7f 84 84  |.4...:..[...s...|
00000140  00 3c e3 2f 06 22 ec 46  f1 3d 91 83 cc 02 22 37  |.<./.".F.=...."7|
00000150  db 40 1e 7d de fe a4 a4  d8 54 d6 f8 30 05 ba bc  |.@.}.....T..0...|
00000160  6e 8e 4b 5b ee f9 af c2  6d 2c b8 df 1b c1 96 1c  |n.K[....m,......|
00000170  df 37 a1 51 de db 50 b1  8d ef 39 57 74 16 df 39  |.7.Q..P...9Wt..9|
00000180  12 26 bd 26 44 92 37 a5  9c 13 c3 a8 c6 f4 32 a4  |.&.&D.7.......2.|
00000190  5a 3d b8 6c 1c df d0 27  7b d4 da 04 a0 53 70 2d  |Z=.l...'{....Sp-|
000001a0  47 79 93 4e 6f 2d a2 a5  e0 c3 0b ad a4 02 c4 38  |Gy.No-.........8|
000001b0  e1 c1 ad cd 75 c1 0d a9  95 bd 60 16 bb 1e 00 00  |....u.....`.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Mark Phelps on 2011-01-24
Sorry no one got back to you on this ... the boot wizards around here are usually more vigilant ...

Have you tried to regenerate the GRUB menu? If not, next time in Ubuntu, open a terminal and enter "sudo update-grub".  Watch it run and see if it mentions Windows or XP.  IF it does, then the new menu will probably work for you.

IF it does not, then go to Places and open the folder that matches your XP partition -- and confirm that the XP boot files are still there.  You need, at a minimum, boot.ini.

---

### Post by bear_jacobsen on 2011-01-24
I solved the problem by first using os-prober and then update the grub.

---

