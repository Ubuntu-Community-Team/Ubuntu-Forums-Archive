---
title: "Ubuntu 10.10. Deleted an unused partition, Grub2 will not boot now"
date: 2011-04-24
forum: General Help
---

### Post by Sun.Dial on 2011-04-24
Good evening,
I have Ubuntu 10.10 and have been a user since 9.04 and am very pleased with the OS indeed, but I always seem to have had problems whenever I alter the structure of my HDD, and subsequently re-boot.
This time I deleted an unused partition to extend a data only partition, and this has renumbered the remaining partitions.

Fortunately I can still boot up into Ubuntu 10.10 by using the **SuperGrub2 Boot Rescue CD** I burned last time this type of thing happened..and I would thoroughly recommend it too.

Luckily I found a reference in the forums to **Boot Info Script 0.55 **by** [meierfra]("http://sourceforge.net/users/meierfra/")**
and this has enabled me to discover quite a lot of information about my present boot arrangements..thanks to **meierfra** for this. Discover yes, and I understand some of it, but the remainder is still a bit of a mystery, so I hope someone can help to direct me as to what to do to get Grub2 back on its feet.

Thank you,
Sun

Here is the o/p from the Boot Info Script:

=================================================
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    50,026,409    50,026,347   7 HPFS/NTFS
/dev/sda2          50,026,471   384,907,263   334,880,793   f W95 Ext d (LBA)
/dev/sda5          50,026,473   166,029,311   116,002,839   b W95 FAT32
/dev/sda6         166,031,838   168,023,834     1,991,997  82 Linux swap / Solaris
/dev/sda7         168,023,898   266,325,569    98,301,672  83 Linux
/dev/sda8         266,326,016   384,907,263   118,581,248  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        48C056F5C056E8A8                       ntfs       WinXP                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        D3DC-88B2                              vfat       XP-MyDocs                     
/dev/sda6        580b03f4-6e03-4c18-98ca-0edde9d6e5a8   swap                                     
/dev/sda7        ea13abe5-44fb-4d98-9d2c-2149805bdf04   ext2                                     
/dev/sda8        60ececdf-3f52-4e95-acb1-f2fc0d6ec3aa   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext2       (rw,errors=remount-ro)
/dev/sda1        /media/WinXP             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/sda5              vfat       (rw,noexec,nosuid,nodev,uid=1000,umask=000)
/dev/sda5        /mnt                     vfat       (rw)
/dev/sda7        /mnt                     ext2       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
insmod tga
if background_image /usr/share/images/grub/Apollo_17_The_Last_Moon_Shot_Edit1.tga ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro  vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro single  vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro  vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro single  vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro  vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro single  vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro  vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04 ro single  vga=771
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set ea13abe5-44fb-4d98-9d2c-2149805bdf04
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 48c056f5c056e8a8
    drivemap -s (hd0) ${root}
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc         proc     nodev,noexec,nosuid          0  0  
#Entry for /dev/sda8 :
UUID=ea13abe5-44fb-4d98-9d2c-2149805bdf04  /             ext2     errors=remount-ro            0  1  
#Entry for /dev/sda1 :
UUID=48C056F5C056E8A8                      /media/WinXP  ntfs-3g  defaults,locale=en_GB.utf8   0  0  
#Entry for /dev/sda5 :
UUID=D3DC-88B2                             /media/sda5   vfat     uid=bb,users,user,umask=000  0  0  
#Entry for /dev/sda7 :
UUID=580b03f4-6e03-4c18-98ca-0edde9d6e5a8  none          swap     sw                           0  0  



=================== sda7: Location of files loaded by Grub: ===================


 132.0GB: boot/grub/core.img
 131.9GB: boot/grub/grub.cfg
 131.8GB: boot/initrd.img-2.6.35-23-generic.dpkg-bak
 131.6GB: boot/initrd.img-2.6.35-24-generic
 131.7GB: boot/initrd.img-2.6.35-25-generic
 131.7GB: boot/initrd.img-2.6.35-27-generic
 131.7GB: boot/initrd.img-2.6.35-28-generic
 131.7GB: boot/vmlinuz-2.6.35-24-generic
 131.6GB: boot/vmlinuz-2.6.35-25-generic
 131.7GB: boot/vmlinuz-2.6.35-27-generic
 131.7GB: boot/vmlinuz-2.6.35-28-generic
 131.7GB: initrd.img
 131.7GB: initrd.img.old
 131.7GB: vmlinuz
 131.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 10 2c 00  |.X.MSWIN4.1...,.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 e9 57 fb 02  |........?....W..|
00000020  17 10 ea 06 27 dd 00 00  00 00 00 00 83 a8 04 00  |....'...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b2 88 dc d3 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  0d 0a 50 57 2f 44 42 20  62 79 20 4b 49 52 20 56  |..PW/DB by KIR V|
000001d0  2e 20 28 43 29 20 50 61  72 61 67 6f 6e 20 31 39  |. (C) Paragon 19|
000001e0  39 37 2d 31 39 39 39 00  00 00 00 00 00 00 00 00  |97-1999.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda7

00000000  7a 38 6c bc 6a 8d 1b 07  34 43 fd 6e b5 4e 2d 68  |z8l.j...4C.n.N-h|
00000010  24 02 b5 60 5d 0a 4d 46  53 6d dc 26 e0 65 4f d7  |$..`].MFSm.&.eO.|
00000020  ee 1f c8 3c 69 5f a1 55  6d 8d 1a 3b dc 38 da de  |...<i_.Um..;.8..|
00000030  57 30 b9 75 b9 20 4c fe  46 d3 8f 48 f4 2e ef f8  |W0.u. L.F..H....|
00000040  ea aa 19 19 9c 1a c7 68  45 e2 2d d3 a2 21 d9 c4  |.......hE.-..!..|
00000050  32 26 d5 5f 7e 68 da 51  dd ce 58 ee de 6b e4 a8  |2&._~h.Q..X..k..|
00000060  f7 cf db 66 8f 9b 09 35  c3 f5 bf 48 c7 65 ee 21  |...f...5...H.e.!|
00000070  e0 f8 00 32 4f ef b0 54  30 40 4c 43 82 f3 43 e4  |...2O..T0@LC..C.|
00000080  69 ff 67 16 bc 81 1e b3  45 77 a8 be 6e 2c 7d e5  |i.g.....Ew..n,}.|
00000090  59 fa 7b 76 69 89 26 15  ae a0 37 ec 74 c0 8c 49  |Y.{vi.&...7.t..I|
000000a0  36 9c 8e db c6 c9 01 d6  d7 d5 84 6e 51 be ee a1  |6..........nQ...|
000000b0  13 ae 6b d3 48 c0 8b 3a  95 0c 2e 25 1f bb 37 99  |..k.H..:...%..7.|
000000c0  17 11 f6 1e 21 8c f5 52  b2 a9 f5 0a 2b 06 6e ff  |....!..R....+.n.|
000000d0  28 7d 70 bf d2 5a 4c ea  bc b9 5f 9d 37 52 1a b7  |(}p..ZL..._.7R..|
000000e0  f1 e1 c1 d6 fd 3f c4 54  b0 d5 9f 7d 6d f5 67 ae  |.....?.T...}m.g.|
000000f0  3a f4 ee 05 27 f5 17 c6  b6 ed 89 ca 44 84 52 a2  |:...'.......D.R.|
00000100  7a 92 ba 9b 1d bd c5 38  cf 62 df 14 7a ed 86 15  |z......8.b..z...|
00000110  0f 12 11 14 05 4e 29 8a  81 36 28 46 56 cc f5 41  |.....N)..6(FV..A|
00000120  43 cc 4b 15 8c 2f f9 48  14 49 27 32 38 b8 5a 30  |C.K../.H.I'28.Z0|
00000130  4c 8b 38 1b 26 86 29 02  77 62 bc 45 2d 64 a8 7d  |L.8.&.).wb.E-d.}|
00000140  35 4b 7c f6 8a cb 46 e5  dc 2b da 98 3e a6 47 51  |5K|...F..+..>.GQ|
00000150  a3 fa ca 6b d5 14 2e 68  d5 16 4e 3c f8 bc c2 b1  |...k...h..N<....|
00000160  ca ab 59 00 50 55 54 4e  5f 69 41 1c 5a 43 25 a2  |..Y.PUTN_iA.ZC%.|
00000170  82 78 35 9b 3b a1 db 08  95 49 35 a0 0d cb 9c 78  |.x5.;....I5....x|
00000180  31 60 f9 16 fd 00 b1 c4  0f 4d cb 95 0c e2 de 92  |1`.......M......|
00000190  7c 14 db 9c a2 1a e2 96  bf 45 4a 49 72 72 d0 e4  ||........EJIrr..|
000001a0  2f 3a dc bb f7 8e 3f dc  93 bd 9e 1c ee 35 a9 fa  |/:....?......5..|
000001b0  2b 70 6d 45 75 f3 35 8c  55 2a 8e 76 35 98 75 b2  |+pmEu.5.U*.v5.u.|
000001c0  e7 59 f8 3a 56 4b b6 50  3b 31 10 75 4d 09 01 37  |.Y.:VK.P;1.uM..7|
000001d0  98 4e c2 08 25 7d 79 07  de 83 a7 62 a2 ef aa 2d  |.N..%}y....b...-|
000001e0  7f 6a 99 34 5e 36 7c db  3e 4f 4d f4 b6 69 83 e8  |.j.4^6|.>OM..i..|
000001f0  75 bf 95 e5 e9 35 d5 08  89 34 3d 48 57 53 34 12  |u....5...4=HWS4.|
00000200

=======================================================
End of post

---

### Post by Sun.Dial on 2011-04-24
Solved thanks to How To by [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945"). Please see:

[SIZE=2]HOWTO: Purge and Reinstall Grub 2 from the Live CD[/SIZE][LEFT][LEFT]
[SIZE=2]http://ubuntuforums.org/showthread.php?t=1581099

In my case, from the early section
[SIZE=1][COLOR=Black]"[/COLOR][/SIZE][/SIZE][SIZE=1][COLOR=Black]**What can I try first?**
[/COLOR][B][COLOR=Black]From the Normal OS (not Live CD).

[/COLOR][COLOR=Black] I used these commands:[/COLOR][/B][/SIZE]sudo grub-install --recheck /dev/sd**X**
sudo update-grub
Thank you,
Sun
 [/LEFT]

[/LEFT]

---

### Post by grahammechanical on 2011-04-24
After deleting that partition you should have run sudo update grub2 before you shutdown. And that (I guess) is what you need to do now. The utility will search for any operating systems and note the partitions they are on. Grub is still using old information. 

Regards.

---

### Post by Sun.Dial on 2011-04-24
Thank you for taking the time to offer help, much appreciated. Regards, Sun

---

