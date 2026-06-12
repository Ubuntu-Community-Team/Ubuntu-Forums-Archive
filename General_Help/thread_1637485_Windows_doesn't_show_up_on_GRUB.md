---
title: "Windows doesn't show up on GRUB"
date: 2010-12-04
forum: General Help
---

### Post by colmeweb on 2010-12-04
I just reinstalled Ubuntu 10.04 (I was running it wubi but various issues prompted me to install it in a separate partition) and now windows isn't an option in the GRUB. I have windows Vista on /dev/sda2 and I can see it on GParted. 

I tried looking through some of the other posts, but I think that I need some direct help with this one. I have tried update-grub and nothing changed.

I don't use Windows often, but it is nice to have the option.

All this is running on a Toshiba Saellite A215

Thanks

---

### Post by jondodson on 2010-12-04
Did you type sudo update-grub or just update-grub.  I think you need the sudo.

---

### Post by sikander3786 on 2010-12-04
If *sudo update-grub* doesn't work,

Please boot an Ubuntu Live CD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us nearly everything we need to know ;-)

Please wrap your output with proper code tags # from post menu. [/code] at the end and [code] at the beginning.

---

### Post by colmeweb on 2011-03-04
Ok, sorry it took so long to get to this. Life got in the way of my computing. The grub update did nothing so I downloaded the boot info script and the output is....

```

       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   228,521,265   225,447,218   7 HPFS/NTFS
/dev/sda3         228,521,982   312,580,095    84,058,114   5 Extended
/dev/sda5         228,521,984   309,043,199    80,521,216  83 Linux
/dev/sda6         309,045,248   312,580,095     3,534,848  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2013 MB, 2013265920 bytes
129 heads, 32 sectors/track, 952 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,932,159     3,932,128   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0C689C0B689BF226                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        5A4CA2994CA26F85                       ntfs       SQ004621V02                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6f46fdb7-b353-43ab-a210-4215a640d299   ext4                                     
/dev/sda6        3ab883ca-3216-405b-9575-d68d6a36995d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1CB8-E2E5                              vfat       C WEBER 2G                    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=6f46fdb7-b353-43ab-a210-4215a640d299 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 6f46fdb7-b353-43ab-a210-4215a640d299
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=6f46fdb7-b353-43ab-a210-4215a640d299 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3ab883ca-3216-405b-9575-d68d6a36995d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 132.2GB: boot/grub/core.img
 132.5GB: boot/grub/grub.cfg
 132.2GB: boot/initrd.img-2.6.32-24-generic
 132.2GB: boot/initrd.img-2.6.32-26-generic
 132.8GB: boot/initrd.img-2.6.32-27-generic
 132.6GB: boot/initrd.img-2.6.32-28-generic
 134.2GB: boot/initrd.img-2.6.32-29-generic
 132.1GB: boot/vmlinuz-2.6.32-24-generic
 132.1GB: boot/vmlinuz-2.6.32-26-generic
 132.4GB: boot/vmlinuz-2.6.32-27-generic
 132.5GB: boot/vmlinuz-2.6.32-28-generic
 133.0GB: boot/vmlinuz-2.6.32-29-generic
 134.2GB: initrd.img
 132.6GB: initrd.img.old
 133.0GB: vmlinuz
 132.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  12 e8 ad 48 8c aa d9 b9  2b 5a bf 2e 5c d6 44 56  |...H....+Z..\.DV|
00000010  fc 7c 55 b9 e9 ea a8 1b  f0 14 57 a0 f9 50 03 81  |.|U.......W..P..|
00000020  ce f7 55 60 fb 54 81 9a  5e 06 90 79 4d 1a 2a d0  |..U`.T..^..yM.*.|
00000030  3b 20 16 56 57 e1 68 fe  97 7c 4b 55 a5 c2 59 77  |; .VW.h..|KU..Yw|
00000040  ac 2e 92 aa 2f aa 00 ef  a8 eb fb 79 55 28 e5 f4  |..../......yU(..|
00000050  ef 08 82 9f f0 3c 5d 4b  a2 8b 3d 83 e2 f1 f2 b9  |.....<]K..=.....|
00000060  52 c5 70 bd 3d c8 3c a9  49 bd ee a9 57 fc 1d e0  |R.p.=.<.I...W...|
00000070  1e 69 ac 8c 92 da 3e c1  f2 8a 24 aa 56 3f f8 28  |.i....>...$.V?.(|
00000080  e8 21 0f 62 af 2a 05 2f  80 ef 7f 77 39 cc 20 5b  |.!.b.*./...w9. [|
00000090  9c 90 d0 e4 eb 9b a0 2b  6b 73 ec 6e 7d f5 ac 03  |.......+ks.n}...|
000000a0  14 41 1f eb 0e 6a 67 0c  dd 5e 33 23 1b d5 c1 30  |.A...jg..^3#...0|
000000b0  0c af e4 1b 50 72 a5 1d  83 12 fd 4c 54 08 40 70  |....Pr.....LT.@p|
000000c0  46 67 54 f6 f3 52 4c c4  a4 e2 d0 73 00 e6 9c 9f  |FgT..RL....s....|
000000d0  e5 60 cd 5a 06 3e ab e5  b3 46 2e 66 7f c0 67 df  |.`.Z.>...F.f..g.|
000000e0  85 97 06 6a 95 5d f7 ab  7c 88 4c b7 41 b6 7a 94  |...j.]..|.L.A.z.|
000000f0  91 ba 0e 7d 44 39 2d dc  96 e3 62 ba a6 7b 29 76  |...}D9-...b..{)v|
00000100  0f fe bd 06 03 52 b0 9c  7e ce fa 28 8c 1f 4a 87  |.....R..~..(..J.|
00000110  9f 50 a7 00 e0 19 ad 6e  35 ab e3 0d 92 17 0f 7f  |.P.....n5.......|
00000120  6c aa bd c0 32 5f 38 04  8b 84 7a 95 58 f3 a4 f2  |l...2_8...z.X...|
00000130  ef fe 3d 1f fc 7a ad 8a  c7 93 17 79 a5 5e 4d 06  |..=..z.....y.^M.|
00000140  6d f3 19 6e 81 9b 9a 58  30 7c 4e c2 1c e3 be 0a  |m..n...X0|N.....|
00000150  48 96 94 0a cd be fa 99  d7 09 b6 4c 98 4d 8a a8  |H..........L.M..|
00000160  df da 9d 42 3a 8d 85 42  ef 46 5b 6c a1 c0 2d ac  |...B:..B.F[l..-.|
00000170  84 43 fa 16 b8 d8 cd 9c  e3 84 dc 68 d9 d4 b6 1c  |.C.........h....|
00000180  2e e6 00 c7 d3 a0 18 e7  2c ac 4a 7d 3a 41 b0 dc  |........,.J}:A..|
00000190  80 e8 db 66 e3 7a 71 c9  d8 2e 06 11 7d 56 2e 2f  |...f.zq.....}V./|
000001a0  96 01 5f 97 28 07 02 91  f7 35 3d 2b d6 8f 03 34  |.._.(....5=+...4|
000001b0  06 fe 25 8f 95 7b fe e2  9f b7 3d 7f b8 e5 00 fe  |..%..{....=.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 a8 cc 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 a8  cc 04 00 f8 35 00 00 00  |............5...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```


Hope that helps, I'm not looking forward to the 3 hr updates that vista is going too throw at me. :shock:

Thanks.

---

### Post by sikander3786 on 2011-03-04
Thanks for the output.

Seems like Grub is detecting your Windows install comfortably.

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


So, can you actually see the Grub menu automatically? There are lots of Ubuntu entries in that menu and Windows (if present) will be at the bottom of Grub menu and you need to scroll down the menu using your arrow keys.

Please let us know if you find it.

It is being named "Windows recovery environment" but that is no big deal. Grub is known to detect Windows Vista, 7 with those names and can be easily fixed later.

---

### Post by colmeweb on 2011-04-02
Thanks for the help. For some reason the first 2 times I chose that my computer went into a detailed disc check. It took 45 min each time and there was no way to cancel it. But third times the charm and I have access to windows now. (My god it takes a long time to boot) Thanks very much.

---

