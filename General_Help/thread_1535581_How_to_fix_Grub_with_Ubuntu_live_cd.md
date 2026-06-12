---
title: "How to fix Grub with Ubuntu live cd"
date: 2010-07-21
forum: General Help
---

### Post by grumpy.biatch on 2010-07-21
Hi,

I've a multiboot set up with Windows7, PCBSD, openSolaris and openSuSE. Added Linux Mint before opensuse (Ubuntu based)with its root on sda7 and home on sda8. 

I edited opensuse grub and added Linux Mint entry in it. When I try to boot Mint, it takes me to Grub 0.97 with windows, pcbsd, solaris  and Mint entries. I can boot everything but Mint. How do I fix this with Ubuntu live cd.

Here is my bootinfoscript result -

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:      Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 178257290 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 594011468 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  
    Boot files/dirs:   
sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007d4a8

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda2         104,856,255   178,256,735    73,400,481  a5 FreeBSD
/dev/sda3         178,257,240   209,712,509    31,455,270  bf Solaris
/dev/sda4    *    209,712,634   625,137,344   415,424,711   5 Extended
/dev/sda5         585,071,298   593,457,164     8,385,867  82 Linux swap / Solaris
/dev/sda6         209,712,636   553,840,874   344,128,239   7 HPFS/NTFS
/dev/sda7         553,840,938   564,331,319    10,490,382  83 Linux
/dev/sda8         564,331,383   585,071,234    20,739,852  83 Linux
/dev/sda9         593,457,228   606,036,059    12,578,832  83 Linux
/dev/sda10        606,036,123   625,137,344    19,101,222  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       667fa098-48d7-4cdf-8dc2-74efc71f70e0   ext4       opensuse home                 
/dev/sda1        79C332AC3B624E50                       ntfs       Windows 7                     
/dev/sda5        21091ed6-e330-446e-9008-984fca760422   swap                                     
/dev/sda6        107472D50E79990C                       ntfs                                     
/dev/sda7        13f325ca-2685-4ea2-b90c-c7e6e4703db9   ext4                                     
/dev/sda8        4e86a813-3fd9-4672-9702-5c4ec569bd91   ext4                                     
/dev/sda9        83295abf-35e1-4b9e-aa32-d0453ba815c6   ext4       opensuse /                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw)
/dev/sda10       /home                    ext4       (rw)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13f325ca-2685-4ea2-b90c-c7e6e4703db9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13f325ca-2685-4ea2-b90c-c7e6e4703db9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 79c332ac3b624e50
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=13f325ca-2685-4ea2-b90c-c7e6e4703db9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=4e86a813-3fd9-4672-9702-5c4ec569bd91 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=21091ed6-e330-446e-9008-984fca760422 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 286.0GB: boot/grub/core.img
 287.2GB: boot/grub/grub.cfg
 287.7GB: boot/initrd.img-2.6.32-21-generic
 287.4GB: boot/vmlinuz-2.6.32-21-generic
 287.7GB: initrd.img
 287.4GB: vmlinuz

=========================== sda9/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Tue Jul 20 18:43:07 SGT 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,8)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 resume=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part5 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows7 Enterprise Edition x64
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title PCBSD 8.0 amd64
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title OpenSolaris 2009.06
    rootnoverify (hd0,2)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title Linux Mint
    rootnoverify (hd0,6)
    chainloader +1

=============================== sda9/etc/fstab: ===============================

/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 /                    ext4       defaults              1 1
/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part10 /home                ext4       defaults              1 2
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda9: Location of files loaded by Grub: ===================


 307.3GB: boot/grub/menu.lst
 304.1GB: boot/grub/stage2
 307.4GB: boot/initrd
 307.4GB: boot/initrd-2.6.31.5-0.1-desktop
 304.9GB: boot/vmlinuz
 304.9GB: boot/vmlinuz-2.6.31.5-0.1-desktop
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea 00 00  ff ff bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
```

Best,

David

---

### Post by dcstar on 2010-07-21
> **grumpy.biatch said:**
> Hi,

I've a multiboot set up with Windows7, PCBSD, openSolaris and openSuSE. Added Linux Mint before opensuse (Ubuntu based)with its root on sda7 and home on sda8. 

I edited opensuse grub and added Linux Mint entry in it.
........

Why?, as stated in **every** GRUB2 HOWTO, just run:
```
sudo update-grub
```
and it will do what it is supposed to do and set up booting entries itself.

---

### Post by grumpy.biatch on 2010-07-21
> **dcstar said:**
> Why?, as stated in **every** GRUB2 HOWTO, just run:
```
sudo update-grub
```
and it will do what it is supposed to do and set up booting entries itself.

Been there done that, doesnt work.

---

### Post by yetiman64 on 2010-07-21
Hi grumpy.biatch, Just noted from the script

> menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8 )" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd**0,8**)' this is from the grub.cfg file (grub2) from the Mint install.

But your entry in the grub 0.97 (From openSuse ?) is pointing to

> title Linux Mint
    rootnoverify (hd**0,6**)
    chainloader +1

 Is this an entry you placed in yourself manually or did openSuse pick up the entry automatically ? It may explain why Mint won't chainload. If you put the openSuse entry in manually you may want to consider trying hd0,7 or hd0,8. Not sure which is the correct one as grub legacy and grub2 handle drive numbering differently as far as I'm aware.

---

### Post by grumpy.biatch on 2010-07-21
> **yetiman64 said:**
> Hi grumpy.biatch, Just noted from the script

 this is from the grub.cfg file (grub2) from the Mint install.

But your entry in the grub 0.97 (From openSuse ?) is pointing to

 Is this an entry you placed in yourself manually or did openSuse pick up the entry automatically ? It may explain why Mint won't chainload. If you put the openSuse entry in manually you may want to consider trying hd0,7 or hd0,8. Not sure which is the correct one as grub legacy and grub2 handle drive numbering differently as far as I'm aware.

I added that manually. Have tried changing sda from 6,7 but no luck so far. I have three Grubs in all, 1 being Grub2 and other are legacy(suse and solaris). The pointing is correct for all Legacy Grub. I guess I now understand whats keeping it from booting - [http://brainstorm.ubuntu.com/item/21151/](http://brainstorm.ubuntu.com/item/21151/)

---

### Post by grumpy.biatch on 2010-07-21
I guess I need to install Grub2 to Mint's / partition. Will that work or it will mess things further.

---

### Post by yetiman64 on 2010-07-21
> **grumpy.biatch said:**
> I guess I need to install Grub2 to Mint's / partition. Will that work or it will mess things further.

I would be careful if you are considering to install grub2 bootloader to a partition boot record, grub2 doesn't seem to work well with blocklists and can cause you further boot problems down the track (especially after a kernel update in Mint).

I have had booting problems on a setup with grub2 in a PBR (partition boot record) and had to revert to grub2 in the MBR.

You could try putting Mint's grub2 in the MBR (it should work with the other systems-check out for compatibility before trying - maybe google the combinations "grub2 with.....".).

Link #2 section 13 in my sig has the grub2 guide directions for that.

---

### Post by drs305 on 2010-07-21
If you are editing the Grub2 menu manually try this entry:
> 
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda7)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	[noparse]set root='(hd0,7)'[/noparse]
	linux	/boot/vmlinuz-2.6.32-21-generic root=/dev/sda7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}


Another way to try this is from the main Grub 2 menu: you can also highlight the entry, press "e" to enter the edit mode, and then manually make the same changes. Once you have made the changes, CTRL-x to boot. The change is not persistent, so you can experiment. You would also have to make the changes and save them once booted.

Manual editing of grub.cfg will end up causing you headaches. If you find a menu entry that works, put it in /etc/grub.d/40_custom or another custom file and then update-grub.

---

### Post by grumpy.biatch on 2010-07-21
> **yetiman64 said:**
> I would be careful if you are considering to install grub2 bootloader to a partition boot record, grub2 doesn't seem to work well with blocklists and can cause you further boot problems down the track (especially after a kernel update in Mint).

I have had booting problems on a setup with grub2 in a PBR (partition boot record) and had to revert to grub2 in the MBR.

You could try putting Mint's grub2 in the MBR (it should work with the other systems-check out for compatibility before trying - maybe google the combinations "grub2 with.....".).

Link #2 section 13 in my sig has the grub2 guide directions for that.


Grub2 doesnt play well ufs and zfs. More information @ [http://brainstorm.ubuntu.com/item/21151/](http://brainstorm.ubuntu.com/item/21151/)

I tried to trick the suse grub by editing Mint boot entry with core.img in order to make suse grub deal with grub2 and mint partitions. Got error 17, file system type not recognized by Grub.

---

### Post by grumpy.biatch on 2010-07-21
> **drs305 said:**
> If you are editing the Grub2 menu manually try this entry:


Another way to try this is from the main Grub 2 menu: you can also highlight the entry, press "e" to enter the edit mode, and then manually make the same changes. Once you have made the changes, CTRL-x to boot. The change is not persistent, so you can experiment. You would also have to make the changes and save them once booted.

Manual editing of grub.cfg will end up causing you headaches. If you find a menu entry that works, put it in /etc/grub.d/40_custom or another custom file and then update-grub.


I am lost............................

---

### Post by grumpy.biatch on 2010-07-21
Here is Mints Grub.conf file prior to suse install 

```
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,8)'
search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=13f325ca-2685-4ea2-b90c-c7e6e4703db9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=13f325ca-2685-4ea2-b90c-c7e6e4703db9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 79c332ac3b624e50
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

I guess I need to trick it a bit on the lines of fresh bootinfoscript. Do I need to change this file alone or various other files with this. I understand Grub2 makes multiple entries in boot and etc places.

---

### Post by drs305 on 2010-07-21
> **grumpy.biatch said:**
> I am lost............................

Perhaps we can help you find your way.

In my previous post, I was asking if you see the Grub2 menu during boot. If you do, pressing a key (down arrow will work) should interrupt the boot sequence and halt at the Grub screen.

Once halted, take a look at the top of the menu. Does it say Grub version 1.97 or later? If so, you are booting with Grub 2.

Next, cursor to the Mint entry. Once highlighted, press "e". That will display the menu entry you currently have for Mint.

Use the up/dn arrows to put the cursor at the start of the "search" line. Hold DEL until the entire line is erased.

On the "set root" line, change it to (hd0,7).
On the linux line, change it to what I have in the previous post (replace UUID with the dev address).

Once you have made those changes and it looks like the entry I posted, press CTRL-x and see if it boots into Mint.

If it does, the menu entry is correct and we can take the next step of permanently incorporating this into your menu.

As was previously mentioned, "update-grub" should have fixed this by automatically finding your OS's and making the correct entries. Since you indicated it did not, we are trying to manually edit things to get it to boot.

---

### Post by grumpy.biatch on 2010-07-21
> **drs305 said:**
> Perhaps we can help you find your way.

In my previous post, I was asking if you see the Grub2 menu during boot. If you do, pressing a key (down arrow will work) should interrupt the boot sequence and halt at the Grub screen.

Once halted, take a look at the top of the menu. Does it say Grub version 1.97 or later? If so, you are booting with Grub 2.

Next, cursor to the Mint entry. Once highlighted, press "e". That will display the menu entry you currently have for Mint.

Use the up/dn arrows to put the cursor at the start of the "search" line. Hold DEL until the entire line is erased.

On the "set root" line, change it to (hd0,7).
On the linux line, change it to what I have in the previous post (replace UUID with the dev address).

Once you have made those changes and it looks like the entry I posted, press CTRL-x and see if it boots into Mint.

If it does, the menu entry is correct and we can take the next step of permanently incorporating this into your menu.

As was previously mentioned, "update-grub" should have fixed this by automatically finding your OS's and making the correct entries. Since you indicated it did not, we are trying to manually edit things to get it to boot.

It says Grub version 0.97. Suse grub replaced Grub2 and Grub legacy does not recognize Grub2 in my case.

I've tried [http://www.dedoimedo.com/computers/grub-2.html#mozTocId542243](http://www.dedoimedo.com/computers/grub-2.html#mozTocId542243) but other than change in error it didnt help much. Is there any way I can boot Mint without compromising suse Grub. I am sure Grub2 wont boot BSD and Solaris.

---

### Post by grumpy.biatch on 2010-07-21
I've found out whats keeping it from boot (thanks to Carl at suse forums).

Grub cnf in sda7

```
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda8) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 13f325ca-2685-4ea2-b90c-c7e6e4703db9
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=13f325ca-2685-4ea2-b90c-c7e6e4703db9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
```
Suse menu.lst

> ###Don't change this comment - YaST2 identifier: Original name: other###
title  Linux Mint
    rootnoverify (hd0,6)
    chainloader +1

Bootinfoscript

```

sda7:   _________________________________________________________________________

     File system:       ext4
    Boot sector type:  -
    Boot sector  info:      Operating System:  Linux Mint 9 Isadora
    Boot  files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img
```I need to change the number at grub.cnf to hd0, 6, how do i do that.

---

### Post by drs305 on 2010-07-21
To be honest, I am not sure where your boot info is coming from. I'll provide several scenarios - it depends which menu you are really trying to select Mint from.

First, see which partitions are currently mounted with this command. The partition with the grub menu will need to be mounted in order to edit it's grub menu. We'll also make a temporary mount point should we need it later:
```

sudo mkdir /mnt/temp
mount | grep /dev/sd
```

Since you say suse took over Grub, your boot menu is Grub legacy (0.97) and menu.lst (Grub legacy's menu) is in sda9, I would suspect you have to edit suse's menu. See if the Mint entry is listed in suse's menu.list. 
**If sda9 is NOT currently mounted (you are not currently booted into suse):**
```
sudo mount /dev/sda9 /mnt/temp
```
Then open /boot/grub/menu.lst for editing, after making a backup. I've used 'nano' since I don't know what text editor you use. Substitute your normal text editor for nano, but make sure you open it as root.
```
sudo cp /mnt/temp/boot/grub/menu.lst /mnt/temp/boot/grub/menu.lst.bak
sudo nano /mnt/temp/boot/grub/menu.lst

```

**If you are already running suse from sda9:**
```
sudo nano /boot/grub/menu.lst
```
If this is menu you are trying to alter, make the changes, save the file, and reboot.

If you really are trying to edit another menu.lst or another menu, the procedure would be the same. 
Identify the correct partition (sda6, sda7, etc).
Make sure the partition is mounted. If not, mount it.
Edit the file, using the complete address: 
```
sudo mount <partition> /mnt/temp
sudo nano /mnt/temp/<path/filename>
```

Again there are caveats about editing grub.cfg (which I suppose is called grub.cnf in suse) but we can temporarily try to make the changes there to try to get a working menu.

---

### Post by grumpy.biatch on 2010-07-21
> **drs305 said:**
> To be honest, I am not sure where your boot info is coming from. I'll provide several scenarios - it depends which menu you are really trying to select Mint from.

First, see which partitions are currently mounted with this command. The partition with the grub menu will need to be mounted in order to edit it's grub menu. We'll also make a temporary mount point should we need it later:
```

sudo mkdir /mnt/temp
mount | grep /dev/sd
```Since you say suse took over Grub, your boot menu is Grub legacy (0.97) and menu.lst (Grub legacy's menu) is in sda9, I would suspect you have to edit suse's menu. See if the Mint entry is listed in suse's menu.list. 
**If sda9 is NOT currently mounted (you are not currently booted into suse):**
```
sudo mount /dev/sda9 /mnt/temp
```Then open /boot/grub/menu.lst for editing, after making a backup. I've used 'nano' since I don't know what text editor you use. Substitute your normal text editor for nano, but make sure you open it as root.
```
sudo cp /mnt/temp/boot/grub/menu.lst /mnt/temp/boot/grub/menu.lst.bak
sudo nano /mnt/temp/boot/grub/menu.lst

```**If you are already running suse from sda9:**
```
sudo nano /boot/grub/menu.lst
```If this is menu you are trying to alter, make the changes, save the file, and reboot.

If you really are trying to edit another menu.lst or another menu, the procedure would be the same. 
Identify the correct partition (sda6, sda7, etc).
Make sure the partition is mounted. If not, mount it.
Edit the file, using the complete address: 
```
sudo mount <partition> /mnt/temp
sudo nano /mnt/temp/<path/filename>
```Again there are caveats about editing grub.cfg (which I suppose is called grub.cnf in suse) but we can temporarily try to make the changes there to try to get a working menu.


@drs, let me sum this up

1. while installing Linux on extended hard disk i created 4 partitions; 2 etx4, 1 swap and 1 ntfs
2. i installed mint on ext partitions with partition # 8 & 9. the gurb.cnf reads (hd0,8 or sda9).
3. later i reszied ntfs and created 2 more ext4 partitions for suse install
4. after suse install the partition order got changed.
5. the other operating systems are on primary partition and were picked up easily by suse grub
6. from suse partitioner i saw mint sitting in sda7 and sda8 and added that entry to boot loader.

Now i wish to mount mint partition and edit grub.cnf in order to replace (hd0, 8 with (hd0,6). Will like to know what else i need to edit to make it work correct. We use kwrite in suse, have gedit as well. 

Best,

david

P.S. - Sorry for the confusion earlier, I got a sense to check the grub.cnf abt couple of hours back and i got here.

---

### Post by oldfred on 2010-07-21
I did not understand how you even booted. But your acer must be a lilo type boot loader that just looks for the active partition (boot flag). You have the boot flag on the extended partition which is unusual but you have a grub legacy install in the extended (it still is a partition so I guess it can have a grub in the PBR).

You issue may be that none of the grub legacy's you have see a ext4 partition. Ubuntu updated it version of grub 0.97 with 9.04 to read ext4 but other distributions may or may not read ext4.

You can install grub2 and let Ubuntu take over booting. You can still chainload to all the old grubs in partitions the same way you now do. Or you have to install a grub to the Ubuntu partition. The issue with blocklist is that if any of the boot files get moved it breaks the boot, since it is loading from a fixed address not file name. You probably could chroot into Ubuntu and install Ubuntu's old grub to the Ubuntu parititon.

---

### Post by grumpy.biatch on 2010-07-21
> **oldfred said:**
> I did not understand how you even booted. But your acer must be a lilo type boot loader that just looks for the active partition (boot flag). You have the boot flag on the extended partition which is unusual but you have a grub legacy install in the extended (it still is a partition so I guess it can have a grub in the PBR).

You issue may be that none of the grub legacy's you have see a ext4 partition. Ubuntu updated it version of grub 0.97 with 9.04 to read ext4 but other distributions may or may not read ext4.

You can install grub2 and let Ubuntu take over booting. You can still chainload to all the old grubs in partitions the same way you now do. Or you have to install a grub to the Ubuntu partition. The issue with blocklist is that if any of the boot files get moved it breaks the boot, since it is loading from a fixed address not file name. You probably could chroot into Ubuntu and install Ubuntu's old grub to the Ubuntu parititon.


@oldfred -

I made a mistake with partitioning and the partition # changed after suse install. Grub inabilities reading Grub2 are not all that important at the moment, I can trick it later. As per booting I can do anything with suse grub (it is more reliable). 

Let me make it simple.

Grub.cnf conf reads Mint / at sda8 but it is actually at sda7. Mint home is sda8. 

I need to edit Grub.cnf in order to set it right. It returns error 13, with some tweaks 15 & 17. 

Best,

David

---

### Post by oldfred on 2010-07-22
Herman has a list of what the errors mean and often solutions. Will suse's grub boot ext4 partition?

Scroll up and he has a table with all the old grub errors:
[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13) 

If when you get a menu can you press e and edit the boot parameters to see if anything works?

---

### Post by grumpy.biatch on 2010-07-22
> **oldfred said:**
> Herman has a list of what the errors mean and often solutions. Will suse's grub boot ext4 partition?

Scroll up and he has a table with all the old grub errors:
[http://members.iinet.net.au/~herman546/p15.html#13]("http://members.iinet.net.au/%7Eherman546/p15.html#13") 

If when you get a menu can you press e and edit the boot parameters to see if anything works?


Suse uses ext4 and its grub can boot anything (the best boot-loader in business). I've already emailed Herman, he is busy with image processing with buntu. 

Best,

David

---

### Post by grumpy.biatch on 2010-07-22
I reinstalled Mint and resolved the partition # contradiction. 

On trying to boot Mint from suse grub got error13, added core.img lines in menu.lst. Now i am getting error 15. Need to replace string root with uuid. How to find uuid for Mint / from suse. 

Any ideas.

---

### Post by drs305 on 2010-07-22
> **grumpy.biatch said:**
> Need to replace string root with uuid. How to find uuid for Mint / from suse. 
Any ideas.

Any linux distro should be able to give you the UUIDs of all partitions with the "blkid" command run as root.

---

### Post by grumpy.biatch on 2010-07-22
> **drs305 said:**
> Any linux distro should be able to give you the UUIDs of all partitions with the "blkid" command run as root.


Drs, 

I managed to get Mint boot from suse legacy grub. Carl, the admin at suse forum helped me out in the process. 

here is my final bootinfoscript -

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ufs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 178257290 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 593941836 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

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

/dev/sda1                  63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda2         104,856,255   178,256,735    73,400,481  a5 FreeBSD
/dev/sda3         178,257,240   209,712,509    31,455,270  bf Solaris
/dev/sda4    *    209,712,634   625,137,344   415,424,711   5 Extended
/dev/sda5         585,071,298   593,457,164     8,385,867  82 Linux swap / Solaris
/dev/sda6         209,712,636   553,840,874   344,128,239   7 HPFS/NTFS
/dev/sda7         553,840,938   564,331,319    10,490,382  83 Linux
/dev/sda8         564,331,383   585,071,234    20,739,852  83 Linux
/dev/sda9         593,457,228   606,036,059    12,578,832  83 Linux
/dev/sda10        606,036,123   625,137,344    19,101,222  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       01e10146-2a9f-48d2-ab76-6577f6c7acc5   ext4       opensuse home                 
/dev/sda11                                              zfs                                      
/dev/sda1        79C332AC3B624E50                       ntfs       Windows 7                     
/dev/sda2                                               ufs                                      
/dev/sda3: PTTYPE="dos" 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        21091ed6-e330-446e-9008-984fca760422   swap                                     
/dev/sda6        107472D50E79990C                       ntfs                                     
/dev/sda7        df03a62e-139e-496f-84c7-12ec186a0d3e   ext4                                     
/dev/sda8        25c1bc7b-af7c-470a-866b-19dd59e73bfc   ext4                                     
/dev/sda9        5e765ca3-29c0-467a-9bd7-d000e6156854   ext4       opensuse /                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /home                    ext4       (rw)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set df03a62e-139e-496f-84c7-12ec186a0d3e
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set df03a62e-139e-496f-84c7-12ec186a0d3e
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set df03a62e-139e-496f-84c7-12ec186a0d3e
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda7)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set df03a62e-139e-496f-84c7-12ec186a0d3e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=df03a62e-139e-496f-84c7-12ec186a0d3e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda7) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set df03a62e-139e-496f-84c7-12ec186a0d3e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=df03a62e-139e-496f-84c7-12ec186a0d3e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set df03a62e-139e-496f-84c7-12ec186a0d3e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set df03a62e-139e-496f-84c7-12ec186a0d3e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 79c332ac3b624e50
    chainloader +1
}
menuentry "Desktop -- openSUSE 11.2 - 2.6.31.5-0.1 (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 83295abf-35e1-4b9e-aa32-d0453ba815c6
    linux /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 resume=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part5 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop
}
menuentry "Failsafe -- openSUSE 11.2 - 2.6.31.5-0.1 (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 83295abf-35e1-4b9e-aa32-d0453ba815c6
    linux /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=df03a62e-139e-496f-84c7-12ec186a0d3e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=25c1bc7b-af7c-470a-866b-19dd59e73bfc /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=21091ed6-e330-446e-9008-984fca760422 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 285.9GB: boot/grub/core.img
 287.3GB: boot/grub/grub.cfg
 287.5GB: boot/initrd.img-2.6.32-21-generic
 287.4GB: boot/vmlinuz-2.6.32-21-generic
 287.5GB: initrd.img
 287.4GB: vmlinuz

=========================== sda9/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Thu Jul 22 18:20:57 SGT 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,8)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 resume=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part5 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.5-0.1
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.31.5-0.1-desktop root=/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 showopts apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.31.5-0.1-desktop

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title PCBSD 8.0 amd64
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title openSolaris 2009.06 i386
    rootnoverify (hd0,2)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: other###
title Linux Mint 9 2.6.32-21-generic
    rootnoverify (hd0,6)
    kernel /vmlinuz root=/dev/sda7 ro quiet splash
    initrd /initrd.img

=============================== sda9/etc/fstab: ===============================

/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part9 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part10 /home                ext4       acl,user_xattr        1 2
/dev/disk/by-id/ata-ST3320418AS_9VMD0YPT-part5 swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda9: Location of files loaded by Grub: ===================


 307.4GB: boot/grub/menu.lst
 304.0GB: boot/grub/stage2
 307.3GB: boot/initrd
 307.3GB: boot/initrd-2.6.31.5-0.1-desktop
 304.3GB: boot/vmlinuz
 304.3GB: boot/vmlinuz-2.6.31.5-0.1-desktop
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea 00 00  ff ff bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200


```

It doesnt read ufs/zfs partitions and returns error. I can now boot everything. 

Lizard is tight!

Best,

David

---

### Post by drs305 on 2010-07-22
:-)

Since there were several of us monitoring this thread, please mark it SOLVED via the *Thread Tools* link at the top right of the first post if you have no further issues.

---

### Post by grumpy.biatch on 2010-07-22
> **drs305 said:**
> :-)

Since there were several of us monitoring this thread, please mark it SOLVED via the *Thread Tools* link at the top right of the first post if you have no further issues.


Did it already.

Thanks for your time.

Have a great day!

---

### Post by Nick_Jinn on 2010-07-22
Subscribes.

---

