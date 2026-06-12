---
title: "Strange Grub behaviour"
date: 2011-02-20
forum: General Help
---

### Post by ciaopaulo on 2011-02-20
Guys,

I'm getting some strange behavior from grub in my new dual boot system.

Grub has started saying "no such partition"

Reinstalls of Win7 / Ubuntu / Grub have no effect.

Feeling despair, I luckily stumbled on a work around: If the Win 7 disk is in the drive then the boot process goes through the "Press key now to boot from CD / DVD..."

Then I get the usual Grub boot selector.

What's going on?!

I'm using Grub 2 on Ubuntu 10.10. 64bit.

---

### Post by Quackers on 2011-02-20
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ciaopaulo on 2011-02-20
Do I need to boot off the live CD? I can get into Ubuntu just fine using the workaround in my first post.

---

### Post by ciaopaulo on 2011-02-20
Here's the RESULTS.txt without going through LiveCD:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    61,439,999    61,233,152   7 HPFS/NTFS
/dev/sda3          61,442,046   117,229,567    55,787,522   5 Extended
/dev/sda5          61,442,048   117,229,567    55,787,520  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2               2,048   398,295,039   398,292,992   f W95 Ext d (LBA)
/dev/sdb5               4,096   204,804,095   204,800,000   7 HPFS/NTFS
/dev/sdb6         204,806,144   398,295,039   193,488,896  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        089C55E29C55CB38                       ntfs       System Reserved               
/dev/sda2        C08E264C8E263AF4                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        313fc39d-83bc-40fc-a80f-bdd7855596c8   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        AA24B46024B430E5                       ntfs       PROG                          
/dev/sdb6        51755b1b-f00a-44dd-992e-820dd8ccd3d3   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb6        /home                    ext4       (rw,commit=0)
/dev/sr0         /media/CD_ROM            iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


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
search --no-floppy --fs-uuid --set 313fc39d-83bc-40fc-a80f-bdd7855596c8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 313fc39d-83bc-40fc-a80f-bdd7855596c8
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 313fc39d-83bc-40fc-a80f-bdd7855596c8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=313fc39d-83bc-40fc-a80f-bdd7855596c8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 313fc39d-83bc-40fc-a80f-bdd7855596c8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=313fc39d-83bc-40fc-a80f-bdd7855596c8 ro single 
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
    search --no-floppy --fs-uuid --set 313fc39d-83bc-40fc-a80f-bdd7855596c8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 313fc39d-83bc-40fc-a80f-bdd7855596c8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 089c55e29c55cb38
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
UUID=313fc39d-83bc-40fc-a80f-bdd7855596c8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=51755b1b-f00a-44dd-992e-820dd8ccd3d3 /home           ext4    defaults        0       2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  46.8GB: boot/grub/core.img
  33.7GB: boot/grub/grub.cfg
  32.2GB: boot/initrd.img-2.6.35-22-generic
  46.8GB: boot/vmlinuz-2.6.35-22-generic
  32.2GB: initrd.img
  46.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  02 00 a0 c0 47 c1 27 ac  12 20 81 cc f1 1c ca 81  |....G.'.. ......|
00000010  5f 00 c8 b6 a4 c3 61 01  25 40 c0 02 80 08 ff c1  |_.....a.%@......|
00000020  02 7d c1 01 e8 40 08 c1  01 c0 53 81 04 c6 00 6d  |.}...@....S....m|
00000030  03 40 02 81 92 43 75 72  72 65 6e 00 74 53 68 69  |.@...Curren.tShi|
00000040  66 74 49 6e 34 66 6f c1  59 65 c0 06 d8 21 35 50  |ftIn4fo.Ye...!5P|
00000050  c8 52 4f 47 d3 07 2e 65  c0 89 dd 31 94 36 e8 d6  |.ROG...e...1.6..|
00000060  71 01 c1 69 37 f0 c0 39  53 d3 17 c2 71 37 01 40  |q..i7..9S...q7.@|
00000070  af f0 00 35 31 53 c0 66  c1 80 c8 85 c7 85 2a c0  |...51S.f......*.|
00000080  2e 40 02 a3 ca a5 33 01  00 76 00 d0 b1 c0 0b 32  |.@....3..v.....2|
00000090  00 2e 40 74 c1 72 30 c0  70 aa 38 40 74 38 c0 03  |..@t.r0.p.8@t8..|
000000a0  39 40 11 36 c0 00 60 31  00 45 00 2d c0 01 41 c1  |9@.6..`1.E.-..A.|
000000b0  74 26 53 c9 1f c7 c9 8e  b9 c0 37 34 f9 98 35 8e  |t&S.......74..5.|
000000c0  b9 d3 27 c2 2f 38 d8 c0  2f 0d c1 27 33 40 18 80  |..'./8../..'3@..|
000000d0  23 00 e0 ac 02 92 00 c1  55 c0 ae c3 29 08 b5 c0  |#.......U...)...|
000000e0  01 00 ba 02 00 48 bb 02  00 60 00 bc 02 00 90 bd  |.....H...`......|
000000f0  02 00 50 f5 c0 6d e8 c0  2d a8 c0 29 cd 77 c1 7d  |..P..m..-..).w.}|
00000100  c1 11 0f 61 00 c0 03 42  00 e1 09 e0 a8 02 00 ff  |...a...B........|
00000110  e5 3b e5 03 e1 02 61 20  61 09 81 43 e1 23 e1 24  |.;....a a..C.#.$|
00000120  e1 e1 11 6c 68 01 00 e1  02 61 02 e1 5b 20 76 6b  |...lh....a..[ vk|
00000130  09 00 c2 00 07 a8 57 02  03 e4 78 00 00 53 68 6f  |......W...x..Sho|
00000140  72 80 74 63 75 74 33 6a  2f 41 0b 4b e2 56 e1 04  |r.tcut3j/A.K.V..|
00000150  4e e0 04 60 b4 e5 2a 00  10 00 43 6c 69 c0 46 20  |N..`..*...Cli.F |
00000160  49 44 80 62 6c 33 91 b8  53 44 e1 76 00 60 e7 02  |ID.bl3..SD.v.`..|
00000170  00 78 f0 02 00 00 b0 6c  03 00 08 8c 03 00 90 90  |.x.....l........|
00000180  d7 03 00 e5 0e 18 a9 e3  92 31 f1 57 30 9a 01 e1  |.........1.W0...|
00000190  7d 20 0c 00 00 50 b0 a5  01 00 01 1c 09 a0 01 98  |} ...P..........|
000001a0  8a 98 e7 1b 20 a2 03 00  00 1c e1 00 07 80 8b e1  |.... ...........|
000001b0  1c 61 04 74 68 65 20 77  38 6f 72 6c e1 32 00 41  |.a.the w8orl.2.A|
000001c0  02 00 07 fe ff ff 00 08  00 00 00 00 35 0c 00 fe  |............5...|
000001d0  ff ff 05 fe ff ff 00 08  35 0c 00 70 88 0b 00 00  |........5..p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-02-20
Which hard drive is set to boot first in the bios? Presumably not the 60GB drive? Try that one.

---

### Post by ciaopaulo on 2011-02-21
Yes the 60GB is set to boot first. I'll check that's the setting in BIOS but I'm 85% sure it is...

...checks...

Well i was 85% wrong.

The Maxtor 200Gb drive was set as first boot. Strange since as it wasn't before. I have some Gigabyte BIOS auto update thing. Wonder if that was the cause.

Anyway, works fine thanks!

---

