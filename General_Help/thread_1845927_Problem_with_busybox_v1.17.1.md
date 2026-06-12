---
title: "Problem with busybox v1.17.1"
date: 2011-09-18
forum: General Help
---

### Post by ayirusp on 2011-09-18
Hi there

I've got this while I've tried to boot into Ubuntu 11.04 Virtual version:
"Alert! dev/disk/by-uuid/62955ca-a0aa-4547-8154-1ad1515c6605 does not exist. Dropping to shell."
"BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) Built-in shell (ash)"

I've been dropped off at this stage. How can I handle with this problem?
Please help me!

Thank you

Ayirusp

---

### Post by Rubi1200 on 2011-09-18
Hi and welcome to the forums :)

Please post the results of the boot info script so we can get a better overview of what is where on the system.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by ayirusp on 2011-09-18
Thank you so much for your quick reply!
Below here is my result text. after running it on my Ubuntu.
However I must say I am very new to Ubuntu, but Ubuntu is challeging to be. Please tell me in details, step by step if any solution available. thank you again for your help.

Ayirusp
```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   204,802,047   204,595,200   7 NTFS / exFAT / HPFS
/dev/sda3         204,802,048   500,986,915   296,184,868   7 NTFS / exFAT / HPFS
/dev/sda4         500,987,902   625,142,447   124,154,546   f W95 Extended (LBA)
/dev/sda5         562,861,215   625,142,447    62,281,233   7 NTFS / exFAT / HPFS
/dev/sda6         558,671,872   562,860,031     4,188,160  82 Linux swap / Solaris
/dev/sda7         500,987,904   554,481,663    53,493,760  83 Linux
/dev/sda8         554,483,712   558,669,823     4,186,112  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192    15,523,839    15,515,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D4D2DA08D2D9EEAC                       ntfs       System Reserved
/dev/sda2        AA22E42D22E3FBE7                       ntfs       
/dev/sda3        EE3E45B13E45741D                       ntfs       
/dev/sda5        01CC6EF562AC3E80                       ntfs       Ubuntu
/dev/sda6        70fe30b2-d60c-4f0d-ae44-54df960a6446   swap       
/dev/sda7        c62955ca-a0aa-4547-8154-1ad1515c6605   ext4       
/dev/sda8        dc459610-de5e-42cc-862d-0261cbdf7517   swap       
/dev/sdb1        04A3-B697                              vfat       PHONE CARD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/PHONE CARD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
set locale_dir=($root)/boot/grub/locale
set lang=th_TH
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
menuentry 'Ubuntu, with Linux 2.6.38-11-virtual' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    linux    /boot/vmlinuz-2.6.38-11-virtual root=UUID=c62955ca-a0aa-4547-8154-1ad1515c6605 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-virtual
}
menuentry 'Ubuntu, with Linux 2.6.38-11-virtual (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    echo    'Loading Linux 2.6.38-11-virtual ...'
    linux    /boot/vmlinuz-2.6.38-11-virtual root=UUID=c62955ca-a0aa-4547-8154-1ad1515c6605 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-virtual
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=c62955ca-a0aa-4547-8154-1ad1515c6605 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=c62955ca-a0aa-4547-8154-1ad1515c6605 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c62955ca-a0aa-4547-8154-1ad1515c6605 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c62955ca-a0aa-4547-8154-1ad1515c6605 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root c62955ca-a0aa-4547-8154-1ad1515c6605
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root D4D2DA08D2D9EEAC
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=dc459610-de5e-42cc-862d-0261cbdf7517 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 245.071151733 = 263.143145472  boot/grub/core.img                             1
 257.212882996 = 276.180230144  boot/grub/grub.cfg                             1
 251.913169861 = 270.489706496  boot/initrd.img-2.6.38-11-generic              2
 245.143917084 = 263.221276672  boot/initrd.img-2.6.38-11-virtual              1
 240.436523438 = 258.166751232  boot/initrd.img-2.6.38-8-generic               2
 240.565742493 = 258.305499136  boot/vmlinuz-2.6.38-11-generic                 1
 250.100959778 = 268.543860736  boot/vmlinuz-2.6.38-11-virtual                 1
 245.069423676 = 263.141289984  boot/vmlinuz-2.6.38-8-generic                  1
 245.143917084 = 263.221276672  initrd.img                                     1
 251.913169861 = 270.489706496  initrd.img.old                                 2
 250.100959778 = 268.543860736  vmlinuz                                        1
 240.565742493 = 258.305499136  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  cb 16 bf 0c 1e 71 55 c2  f9 5c 7d f9 dc bc cf a2  |.....qU..\}.....|
00000010  88 5b 15 e2 d6 58 c5 ed  59 ef 51 37 c8 92 36 ec  |.[...X..Y.Q7..6.|
00000020  4e 47 ee c5 8a 64 a7 1e  7e 91 c8 68 3c 20 54 e6  |NG...d..~..h< T.|
00000030  64 ae 0a b8 7c 21 62 3e  0d e1 5a bc 94 7c 0b 64  |d...|!b>..Z..|.d|
00000040  48 7d 14 97 a7 ae d1 8c  da 96 6e 38 e5 51 b0 8e  |H}........n8.Q..|
00000050  ab b2 b0 0d b9 c1 48 9a  f2 78 61 b1 f8 db 0f e1  |......H..xa.....|
00000060  70 60 76 9c 14 a1 86 4f  94 64 85 d3 48 ee 65 2f  |p`v....O.d..H.e/|
00000070  b1 ad f1 99 cc 29 c7 e4  30 4a 1f 1f 03 ef 63 98  |.....)..0J....c.|
00000080  ba d5 a0 2f ab c9 b5 e8  6e 30 67 e5 0e d8 32 98  |.../....n0g...2.|
00000090  0c 27 f5 59 30 86 72 40  29 2d 8c 50 00 37 69 fa  |.'.Y0.r@)-.P.7i.|
000000a0  5b 05 59 ea 8a f6 90 1e  6e 70 ad 59 25 2d 18 df  |[.Y.....np.Y%-..|
000000b0  90 e5 26 87 a1 47 18 0f  81 39 e0 cf 7c 70 c0 bb  |..&..G...9..|p..|
000000c0  c7 54 ab a9 0e 38 86 ef  d8 dd 30 58 b9 4a 58 57  |.T...8....0X.JXW|
000000d0  51 ef 2b 9d 1e 1c ca f3  1f c4 97 69 45 99 4a ce  |Q.+........iE.J.|
000000e0  b3 6a dd 86 d3 da 49 a1  33 6d 08 4e 39 cf 73 91  |.j....I.3m.N9.s.|
000000f0  a5 8b ed 57 e2 f1 da d2  27 66 67 26 66 f2 27 64  |...W....'fg&f.'d|
00000100  15 2e 7a db b6 6f c9 b6  41 56 8e e5 50 9c 2b 60  |..z..o..AV..P.+`|
00000110  21 41 96 af 6b f7 d7 cd  fc f4 49 53 2d fa b8 f0  |!A..k.....IS-...|
00000120  20 c6 4a 45 d3 c3 39 ef  08 0f 5b 09 e9 ce 7e d7  | .JE..9...[...~.|
00000130  98 d6 8e e0 75 9d 94 47  46 86 77 78 26 6e 9e 27  |....u..GF.wx&n.'|
00000140  49 9a 54 9c 89 e6 06 52  cc 4f 47 e3 35 c4 ae 49  |I.T....R.OG.5..I|
00000150  21 52 7e 65 fc 91 1f e2  e7 72 68 63 1f 4e b9 f9  |!R~e.....rhc.N..|
00000160  45 50 e3 fc 73 27 e3 1f  14 0d 6c e0 9e 1e 3d 49  |EP..s'....l...=I|
00000170  0f fb 4e f7 40 c1 ca 82  06 4f d6 1c 23 d8 2b 9b  |..N.@....O..#.+.|
00000180  0a ce 7f c0 6d 13 c1 d9  a2 7f 22 a9 d0 b9 e9 a8  |....m.....".....|
00000190  f6 59 28 94 b9 5e 27 48  05 f4 ba ef 7f 8c 54 7e  |.Y(..^'H......T~|
000001a0  cb 3d f0 84 96 7a d0 45  7c 1d 01 29 ba b4 b6 7c  |.=...z.E|..)...||
000001b0  ae 31 73 74 28 d3 05 98  8b 78 4c 67 c1 28 00 03  |.1st(....xLg.(..|
000001c0  ff ff 07 03 ff ff a1 1c  b0 03 11 56 b6 03 00 07  |...........V....|
000001d0  ff ff 05 07 ff ff 2a 2e  70 03 d8 e9 3f 00 00 00  |......*.p...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 de 09  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 c0 ec 00 11 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 97 b6 a3 04 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
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


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by oldfred on 2011-09-18
This part is true as you do not now have this UUID.
> dev/disk/by-uuid/62955ca-a0aa-4547-8154-1ad1515c6605 does not exist.

This is now your sda7:
/dev/sda7        c62955ca-a0aa-4547-8154-1ad1515c6605   ext4 

Did you install once and then reinstall? It looks like you have an old grub2 boot loader looking for the wrong UUID even though it is still sda7. It also looks like you edited fstab to use device /dev/sda7 not the UUID. UUID is preferred as it actually changes less often then the device. (But not in your case, obviously).

I would just reinstall grub2's boot loader to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

