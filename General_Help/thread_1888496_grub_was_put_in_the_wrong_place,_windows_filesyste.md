---
title: "grub was put in the wrong place, windows filesystem failed"
date: 2011-11-29
forum: General Help
---

### Post by kochemoh on 2011-11-29
Hello Guys!
I know that there is a lot of information about grub2 and dual boot installations and most probably I read it all today :), however I didn't manage to find any solution in my case. 

1) vista partition is shown as "unknown filesystem" I assume device entry is missing, originally it was SDA2

2) ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   315645119   156285536    7  HPFS/NTFS/exFAT
/dev/sda3       315645182   625141759   154748289    5  Extended
/dev/sda5       315645184   546108794   115231805+   7  HPFS/NTFS/exFAT
/dev/sda6       546109440   565639167     9764864   82  Linux swap / Solaris
/dev/sda7       565641216   625141759    29750272   83  Linux

```

3) ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 64. But according to the info from fdisk, 
                       sda5 starts at sector 315645184.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda7 and looks at sector 620449104 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #7 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   315,645,119   312,571,072   7 NTFS / exFAT / HPFS
/dev/sda3         315,645,182   625,141,759   309,496,578   5 Extended
/dev/sda5         315,645,184   546,108,794   230,463,611   7 NTFS / exFAT / HPFS
/dev/sda6         546,109,440   565,639,167    19,529,728  82 Linux swap / Solaris
/dev/sda7         565,641,216   625,141,759    59,500,544  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2652983252980927                       ntfs       WinRE
/dev/sda5        ACE29CCCE29C9C60                       ntfs       Data
/dev/sda6        983b8070-6767-45ee-a902-12486d43db11   swap       
/dev/sda7        3d360a8f-521f-48a9-adb4-858ae73c7ad6   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d360a8f-521f-48a9-adb4-858ae73c7ad6

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 11.10, kernel 3.0.0-13-generic
uuid		3d360a8f-521f-48a9-adb4-858ae73c7ad6
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro quiet splash 
initrd		/boot/initrd.img-3.0.0-13-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
uuid		3d360a8f-521f-48a9-adb4-858ae73c7ad6
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro  single
initrd		/boot/initrd.img-3.0.0-13-generic

title		Ubuntu 11.10, kernel 3.0.0-12-generic
uuid		3d360a8f-521f-48a9-adb4-858ae73c7ad6
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro quiet splash 
initrd		/boot/initrd.img-3.0.0-12-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
uuid		3d360a8f-521f-48a9-adb4-858ae73c7ad6
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro  single
initrd		/boot/initrd.img-3.0.0-12-generic

title		Chainload into GRUB 2
root		3d360a8f-521f-48a9-adb4-858ae73c7ad6
kernel		/boot/grub/core.img

title		Ubuntu 11.10, memtest86+
uuid		3d360a8f-521f-48a9-adb4-858ae73c7ad6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

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
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos7)'
  search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos7)'
	search --no-floppy --fs-uuid --set=root 3d360a8f-521f-48a9-adb4-858ae73c7ad6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root 12929A49929A3169
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=3d360a8f-521f-48a9-adb4-858ae73c7ad6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=983b8070-6767-45ee-a902-12486d43db11 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 274.496692657 = 294.738579456  boot/grub/core.img                             1
 295.853187561 = 317.669941248  boot/grub/grub.cfg                             1
 280.033588409 = 300.683776000  boot/grub/menu.lst                             1
 295.853553772 = 317.670334464  boot/grub/stage2                               1
 288.098628998 = 309.343547392  boot/initrd.img-3.0.0-12-generic               2
 271.903327942 = 291.953975296  boot/initrd.img-3.0.0-13-generic               1
 295.851215363 = 317.667823616  boot/vmlinuz-3.0.0-12-generic                  1
 270.644943237 = 290.602795008  boot/vmlinuz-3.0.0-13-generic                  1
 271.903327942 = 291.953975296  initrd.img                                     1
 288.098628998 = 309.343547392  initrd.img.old                                 2
 270.644943237 = 290.602795008  vmlinuz                                        1
 295.851215363 = 317.667823616  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  33 c0 fa 8e d8 8e d0 bc  00 7c 89 e6 06 57 8e c0  |3........|...W..|
00000010  fb fc bf 00 06 b9 00 01  f3 a5 ea 1f 06 00 00 52  |...............R|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 21 01 4d 69  |.RPf1.f..f..!.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 8d 64 10 66  |..A......{...d.f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 62 00 4d 75 6c  |.......fa..b.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 13 81 3e fe 7d 55  |F.f.D..0.r..>.}U|
00000150  aa 0f 85 06 ff bc fa 7b  5a 5f 07 fa ff e4 e8 1e  |.......{Z_......|
00000160  00 4f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  |.Operating syste|
00000170  6d 20 6c 6f 61 64 20 65  72 72 6f 72 2e 0d 0a 5e  |m load error...^|
00000180  ac b4 0e 8a 3e 62 04 b3  07 cd 10 3c 0a 75 f1 cd  |....>b.....<.u..|
00000190  18 f4 eb fd 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  4d 47 52 20 69 73 20 63  |........MGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200



```

That was my attempt to fix the dual boot. As well I was smart enough to lock my working drive with documents I need urgently. 
I'm noob to linux, but I hope to get use to it, cause I like it, even after 8 hours nonstop of digging for solution. 

Thank you,
Sergey

---

### Post by deonis on 2011-11-29
Hi Serega, 

We will need some more information about your installation. Are you able to boot in anything, Ubuntu, Windows? 

cheers

denis

---

### Post by kochemoh on 2011-11-29
> **deonis said:**
> Hi Serega, 

We will need some more information about your installation. Are you able to boot in anything, Ubuntu, Windows? 

cheers

denis

Hi, Denis!

Yes, I can boot ubuntu, but have no rescue CD/DVD for windows, cause it's bloody laptop.
KR, S

---

### Post by oldfred on 2011-11-29
You seem to have grub legacy & grub2 installed as you have both menu.lst and grub.cfg. You are booting with grub legacy in the MBR.

Partition table shows sda2 as NTFS (07), but NTFS partitions have to have the Partition boot sector (PBR) with a NTFS configuration. If you have a Windows repairCD or USB you use these commands to fix the PBR.

chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands

NTFS partitions keep a backup PBR. Testdisk can be used to recover the backup or rebuild a basic NTFS PBR. But the testdisk version usually is not bootable with Vista/7 without chkdsk & fixboot, so hopefully the backup is good and not also overwritten.

Testdisk is in the Ubuntu repository, do you can directly download it to a working Ubuntu or LiveCD.

This is instructions on doing the repair. Based on those who installed grub to the PBR, but the fix is the same.
Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by deonis on 2011-11-29
You will need to restore your vista Bootloader and the easiest way of doing that is to use Bootable WinVista CD. There are few other program on the internet which you can use, but most of them are commercial. So your best way will be to get a CD with WinVista. As for your unknown partition, how did you create it ? Were you using some sort of a program or Windows Administrator tools?

---

### Post by Mark Phelps on 2011-11-29
Few comments ...

Vista does not come on a CD; therefore, there is no such thing as a WinVista CD.  Plus, it hasn't been sold commercially for years.  So, your chances of finding a Vista DVD are very slim.

Oldfred provided the detail instructions you need to follow to repair your Vista setup so it will work again. You need to use Testdisk in the manner he stated.

If testdisk doesn't work, what you can then try is using Boot-Repair.  It's also likely to NOT work -- but it's worth a try. See the link below:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

You can also try using the Partition Wizard Boot CD to repair your Vista install.  Google for that, download the ISO image, burn it to CD, and then boot from that.

---

### Post by deonis on 2011-12-01
I just did a quick search for Recovery CD for winvista and here it is, just 6.99$: 

[https://www.google.com/search?q=winvista+recovery+cd&hl=en&client=ubuntu&hs=hU0&channel=fs&prmd=imvns&source=univ&tbm=shop&tbo=u&sa=X&ei=RhTXTue2Cajd0QGci9ntDQ&ved=0CF4QrQQ&biw=1280&bih=609](https://www.google.com/search?q=winvista+recovery+cd&hl=en&client=ubuntu&hs=hU0&channel=fs&prmd=imvns&source=univ&tbm=shop&tbo=u&sa=X&ei=RhTXTue2Cajd0QGci9ntDQ&ved=0CF4QrQQ&biw=1280&bih=609)

---

### Post by oldfred on 2011-12-01
There are recovery CDs from the vendor of you system that are an image of your hard drive as purchased. Most vendors charge at least a shipping fee.
There is the Windows repair CD which Microsoft may also call a recoveryCD.

If you know someone else with the same 32 or 64 bit version.


Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Another download site Despotism Believed to be ok.
[http://ubuntuforums.org/showpost.php?p=11249721&postcount=439](http://ubuntuforums.org/showpost.php?p=11249721&postcount=439)
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links (Now $10.00):
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by deonis on 2011-12-01
nice info :)

---

