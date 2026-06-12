---
title: "Just installed, cannot run!"
date: 2011-01-10
forum: General Help
---

### Post by Pard68 on 2011-01-10
I just finished my Ubuntu install (dualboot w/ Win7). I clicked the restart option once the install finished and picked the regular boot (not the safeboot). It ran through the grub fine enough. Then I got to a point w/ an error message (before the login screen popped up). The message read

"gconf2-sanity-check-2 exited with status 256"

There was a location in front of that but I cannot recall it. I exited it out and the login popped. In the top right corner a thing came up saying that some power management didn't start and I should contact my administrator.

I ignored it and logged in. A few seconds later the original error message popped back up. When I clicked it out I was presented with the login screen all over. I went through this a few times and decided it was useless. 

I only tried logging in with GNOME and the safe version of GNOME. 

Right now I am running a LiveCD, is there anything I can do to fix this, short of reinstalling it?

---

### Post by Quackers on 2011-01-10
From the Live cd desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by DogMatix on 2011-01-10
Could be a permissions issue. See here [http://ubuntuforums.org/showthread.php?t=917306](http://ubuntuforums.org/showthread.php?t=917306)

---

### Post by Pard68 on 2011-01-10
OK here it is. I think my issue may be that the 50gb partition is already full. Trying to delete stuff, but cannot figure out how to delete the files. Probably a permissions issue.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   504,212,373   501,138,326   7 HPFS/NTFS
/dev/sda3         606,115,840   625,141,759    19,025,920  17 Hidden HPFS/NTFS
/dev/sda4         504,213,502   606,115,839   101,902,338   5 Extended
/dev/sda5         504,213,504   601,855,999    97,642,496  83 Linux
/dev/sda6         601,858,048   606,115,839     4,257,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A0C6477EC64753A6                       ntfs       System                        
/dev/sda2        C2A86D44A86D37D5                       ntfs       TI105487W0B                   
/dev/sda3        7C169388169341D6                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4f3bdd76-6616-4d84-9570-a69918fe752c   ext4                                     
/dev/sda6        c53f275c-11d1-48af-bef2-bc77835c113a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/4f3bdd76-6616-4d84-9570-a69918fe752c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/TI105487W0B       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 4f3bdd76-6616-4d84-9570-a69918fe752c
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
search --no-floppy --fs-uuid --set 4f3bdd76-6616-4d84-9570-a69918fe752c
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f3bdd76-6616-4d84-9570-a69918fe752c
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4f3bdd76-6616-4d84-9570-a69918fe752c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f3bdd76-6616-4d84-9570-a69918fe752c
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4f3bdd76-6616-4d84-9570-a69918fe752c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f3bdd76-6616-4d84-9570-a69918fe752c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 4f3bdd76-6616-4d84-9570-a69918fe752c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a0c6477ec64753a6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c2a86d44a86d37d5
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7c169388169341d6
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
UUID=4f3bdd76-6616-4d84-9570-a69918fe752c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c53f275c-11d1-48af-bef2-bc77835c113a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 271.1GB: boot/grub/core.img
 275.4GB: boot/grub/grub.cfg
 273.2GB: boot/initrd.img-2.6.32-24-generic
 271.1GB: boot/vmlinuz-2.6.32-24-generic
 273.2GB: initrd.img
 271.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  91 6a ef 65 63 f8 7d 4c  37 22 4a 45 6e 59 52 69  |.j.ec.}L7"JEnYRi|
00000010  8b a3 d0 1b 38 94 5d 99  8a 79 5b d2 85 d6 94 78  |....8.]..y[....x|
00000020  e3 13 1f 55 11 72 84 e2  7b 44 1f 16 09 5d ca 7c  |...U.r..{D...].||
00000030  e9 c5 b6 88 90 b0 9a 2b  fb b0 10 a5 3b 2a 3b 9b  |.......+....;*;.|
00000040  30 07 ae 69 95 ab 89 b9  3c 2b e5 55 9b ba 73 39  |0..i....<+.U..s9|
00000050  88 65 5f ed 41 01 7b 11  af 61 99 39 ec cc 38 fc  |.e_.A.{..a.9..8.|
00000060  02 ad 64 48 f6 8d d7 f8  05 3f 64 a9 2d 5a 96 c9  |..dH.....?d.-Z..|
00000070  ef ed 94 f0 54 6d 47 74  2e f2 bf 38 a0 a3 d3 c4  |....TmGt...8....|
00000080  e0 6f 08 9b 3c ff b5 c8  5b e8 64 bb c6 24 7a 53  |.o..<...[.d..$zS|
00000090  a6 c3 1b 3c d0 de 48 7b  fe cd 4a 47 5f 99 54 1b  |...<..H{..JG_.T.|
000000a0  53 b4 64 09 6f e8 6a 51  c8 8e ac 32 6e 00 69 00  |S.d.o.jQ...2n.i.|
000000b0  36 51 bc 77 bd 3b c4 4f  a9 58 02 10 32 95 02 28  |6Q.w.;.O.X..2..(|
000000c0  e2 e5 3e 3b 98 32 3f ba  d3 99 05 b7 2d d6 a9 f8  |..>;.2?.....-...|
000000d0  26 fd 41 4a 23 6c 04 17  b7 fd af 3b 20 80 27 14  |&.AJ#l.....; .'.|
000000e0  15 68 5f d8 bf c4 7c 2c  05 71 37 f2 0c 8e 83 62  |.h_...|,.q7....b|
000000f0  fe 31 70 5c 0b 58 50 fc  ae 23 18 70 32 40 09 06  |.1p\.XP..#.p2@..|
00000100  74 a6 8f 89 ea 86 69 ce  e4 7e 0a 8a 12 11 3f 66  |t.....i..~....?f|
00000110  47 54 13 56 7c e9 f0 26  18 31 06 56 6f be f0 27  |GT.V|..&.1.Vo..'|
00000120  88 07 95 f6 23 60 4d c9  fa 29 46 28 48 45 25 2e  |....#`M..)F(HE%.|
00000130  88 ce f0 df 7f 06 2b bc  7c 91 41 95 df e2 26 9f  |......+.|.A...&.|
00000140  d8 f4 3b c6 71 3a 72 44  cf d8 b2 73 b4 13 7d df  |..;.q:rD...s..}.|
00000150  49 06 d0 a0 1b 97 4a e7  63 aa 91 d6 8a 95 f2 95  |I.....J.c.......|
00000160  ec d3 47 a2 dd fc 1e 68  e9 f4 17 14 60 63 8e a4  |..G....h....`c..|
00000170  13 66 7a 40 58 85 95 ce  54 e4 be c1 79 bd 9b 31  |.fz@X...T...y..1|
00000180  4d 0d 82 31 6d 8e 9a 5d  d2 e6 3d b2 54 1e a1 a3  |M..1m..]..=.T...|
00000190  6c 55 b8 68 3e b6 54 9a  d7 a7 8f fd b3 43 6a 9d  |lU.h>.T......Cj.|
000001a0  82 0b b4 1c 2b d8 2e 4a  12 15 ec f6 97 2a fe 04  |....+..J.....*..|
000001b0  df 3b 50 c0 d6 13 cf 72  74 5b cd 33 40 10 00 fe  |.;P....rt[.3@...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e8 d1 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e8  d1 05 00 00 41 00 00 00  |............A...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

 
```

---

### Post by Quackers on 2011-01-10
I don't see anything wrong with the boot script output.
Did you see the link that DogMatix posted in post #3?

---

### Post by Pard68 on 2011-01-10
OK, thanks guys. I figured it out. Loaded up in safe mode and just deleted directories in my documents folder until startx would load without a fail. 

Now I got to figure out how to disable my stupid touchpad...

---

