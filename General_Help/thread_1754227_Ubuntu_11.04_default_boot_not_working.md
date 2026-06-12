---
title: "Ubuntu 11.04 default boot not working"
date: 2011-05-09
forum: General Help
---

### Post by insanekat on 2011-05-09
Just upgraded to 11.04 and for some ungodly reason it won't boot to the first kernel in the boot loader (I dual boot Windows 7). I must go to Previous Versions of Linux then a different kernel and everything works fine. I tried to put this different menu option as default for booting so that if I walk away from my computer while it's starting up, no big deal. However, it hasn't changed the option.

My input:
```
sudo gedit /etc/default/grub
```

at the ...DEFAULT= I input: 2>2 (no quotes...)so that it would highlight the proper one, however nothing. Did the update-grub, restart and it was still in the same spot as before. I also tried the graphical Start-up manager with no results.

I must be doing something incorrectly but I'm not savvy enough to figure it out so any thoughts are appreciated!

---

### Post by wilee-nilee on 2011-05-09
So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This is a what is where and quite helpful,your description is missing a few things, no big deal.;)

---

### Post by insanekat on 2011-05-09
Yeah sorry I wasn't too sure what to include... 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   100,018,974    99,609,375   7 HPFS/NTFS
/dev/sda3       1,432,502,272 1,464,936,447    32,434,176   7 HPFS/NTFS
/dev/sda4         100,020,222 1,432,500,223 1,332,480,002   5 Extended
/dev/sda5         100,020,224   100,995,071       974,848  83 Linux
/dev/sda6         100,997,120   120,526,847    19,529,728  83 Linux
/dev/sda7         120,528,896   124,432,383     3,903,488  82 Linux swap / Solaris
/dev/sda8         124,434,432 1,432,500,223 1,308,065,792  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00D29D05D29D0058                       ntfs       SYSTEM                        
/dev/sda2        C81C96AE1C9696D2                       ntfs                                     
/dev/sda3        DC98B44C98B426C4                       ntfs       RECOVERY                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c5d098ae-dd08-4140-8804-6fd6fffecf64   ext2                                     
/dev/sda6        32a1a661-1bbd-41a8-a60d-a4a4067526e5   ext4                                     
/dev/sda7        9b87a354-5985-45a4-a441-537c81525bae   swap                                     
/dev/sda8        90d341f1-8355-4faa-b9c7-435cb2dd1249   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /boot                    ext2       (rw)
/dev/sda8        /home                    ext4       (rw,commit=0)


============================= sda5/grub/menu.lst: =============================

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
# kopt=root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c5d098ae-dd08-4140-8804-6fd6fffecf64

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

title		Ubuntu 11.04, kernel 2.6.35-28-generic
uuid		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro quiet splash 
initrd		/initrd.img-2.6.35-28-generic

title		Ubuntu 11.04, kernel 2.6.35-28-generic (recovery mode)
uuid		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro  single
initrd		/initrd.img-2.6.35-28-generic

title		Chainload into GRUB 2
root		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/boot/grub/core.img

title		Ubuntu 11.04, memtest86+
uuid		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

============================= sda5/grub/grub.cfg: =============================

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
set default="4"
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 32a1a661-1bbd-41a8-a60d-a4a4067526e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
set locale_dir=($root)/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.38-8-generic-pae root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/vmlinuz-2.6.38-8-generic-pae root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.38-8-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 00D29D05D29D0058
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root C81C96AE1C9696D2
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root DC98B44C98B426C4
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

=================== sda5: Location of files loaded by Grub: ===================


  51.5GB: grub/core.img
  51.5GB: grub/grub.cfg
  51.5GB: grub/menu.lst
  51.2GB: initrd.img-2.6.35-22-generic
  51.2GB: initrd.img-2.6.35-28-generic
  51.2GB: initrd.img-2.6.38-8-generic
  51.3GB: initrd.img-2.6.38-8-generic-pae
  51.2GB: vmlinuz-2.6.35-22-generic
  51.2GB: vmlinuz-2.6.35-28-generic
  51.2GB: vmlinuz-2.6.38-8-generic
  51.2GB: vmlinuz-2.6.38-8-generic-pae

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=c5d098ae-dd08-4140-8804-6fd6fffecf64 /boot           ext2    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=90d341f1-8355-4faa-b9c7-435cb2dd1249 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=9b87a354-5985-45a4-a441-537c81525bae none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  51.8GB: initrd.img
  51.7GB: initrd.img.old
  51.7GB: vmlinuz
  51.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 0e 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e0  0e 00 00 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5

00000000  eb 63 90 ff ff ff ff ff  ff ff ff ff ff ff ff ff  |.c..............|
00000010  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000050  ff ff ff ff ff ff ff ff  ff ff 00 80 a8 f4 fe 05  |................|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  ff ff ff ff ff ff ff ff  |...<.u..........|
000001c0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001f0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2011-05-09
So I suspect your using easybcd is this correct?

You also have grub-legacy and grub2 installed, this is not advised. 

It looks like you have tried setting up sda5 as a boot partition, is this all correct?

```
sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   **/grub/menu.lst** /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________
```

I highlighted the grub-legacy.

---

### Post by insanekat on 2011-05-09
Yes to easybcd. I guess yes to the grub legacy and grub 2? As for sda5 I just followed instructions for dual booting Windows 7 and Ubuntu 10.10! So yes? As you can tell, I'm quite in the dark in this area.

---

### Post by wilee-nilee on 2011-05-09
> **insanekat said:**
> Yes to easybcd. I guess yes to the grub legacy and grub 2? As for sda5 I just followed instructions for dual booting Windows 7 and Ubuntu 10.10! So yes? As you can tell, I'm quite in the dark in this area.

Cool I have let another member know of your thread they are very good in the easybcd area, OS's and Ubuntu, I suspect they will post.

---

### Post by insanekat on 2011-05-09
Thanks! I appreciate it! No rush though, I can still run Ubuntu and Windows fine, it's just a bit inconvenient when rebooting/turning on the laptop.

---

### Post by jtarin on 2011-05-09
I can help but you'll have to wait until I get home....several hours I'm afraid. Why am I looking at 3 Windows partitions.....are they all bootable? attach a screen of your EasyBCD menu list so I can get an idea of what your trying to boot.

---

### Post by insanekat on 2011-05-10
Which part of EasyBCD would you like?

The first one is the Windows 7, one of them is recovery and the other is system information or something like that I believe.

---

### Post by wilee-nilee on 2011-05-10
> **insanekat said:**
> Which part of EasyBCD would you like?

The first one is the Windows 7, one of them is recovery and the other is system information or something like that I believe.

You have a boot partition=sda1
The OS=sda2
The recovery=sda3

This is a oem install it looks like, this and a number of variations with vendors is always fun to figure out.;)

So @insanekat post screen shots of any screen shot relative from the easybcd app, sometimes helpers are busy with work and life. So if you can make it easier for them it will go faster for you. It's hard to know I realise, which one but you can't really fail here with as many as possible. Use the paper clip in the reply panel to upload them and place them on in the reply, they will then just be a small, and click-able, and will run in sequence.

Hope this is okay just wanted to add anything that might make it easier in general.;)

---

### Post by insanekat on 2011-05-10
Thanks, I'll do that ASAP. I always want to give more information I'm just never sure what to give! Maybe it's better to have too much?

---

### Post by wilee-nilee on 2011-05-10
> **insanekat said:**
> Thanks, I'll do that ASAP. I always want to give more information I'm just never sure what to give! Maybe it's better to have too much?

It is always a balancing act so to speak, but your on the right track I think.

---

### Post by insanekat on 2011-05-10
```
There are a total of 2 entries listed in the bootloader.

Default: Ubuntu 11.04
Timeout: 30 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Ubuntu 11.04
BCD ID: {default}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub0.mbr

Entry #2
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe
```

```
Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
extendedinput           Yes
default                 {dbc344f5-70fe-11e0-8f93-e9b8ef9ba288}
resumeobject            {dbc344ed-70fe-11e0-8f93-e9b8ef9ba288}
displayorder            {dbc344f5-70fe-11e0-8f93-e9b8ef9ba288}
                        {dbc344ee-70fe-11e0-8f93-e9b8ef9ba288}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 30
displaybootmenu         Yes
customactions           0x1000085000001
                        0x5400000f
custom:5400000f         {dbc344f3-70fe-11e0-8f93-e9b8ef9ba288}

Real-mode Boot Sector
---------------------
identifier              {dbc344f5-70fe-11e0-8f93-e9b8ef9ba288}
device                  partition=C:
path                    \NST\AutoNeoGrub0.mbr
description             Ubuntu 11.04

Windows Boot Loader
-------------------
identifier              {dbc344ee-70fe-11e0-8f93-e9b8ef9ba288}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
recoverysequence        {dbc344f3-70fe-11e0-8f93-e9b8ef9ba288}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {dbc344ed-70fe-11e0-8f93-e9b8ef9ba288}
nx                      OptIn
detecthal               Yes
```

---

### Post by jtarin on 2011-05-10
Now looking at this I can only surmise it's not an EasyBCD configuration but something with Grub. If you have more than one kernel entry on your prefered Grub menu why don't you just remove them and the kernels associated with that/those entries?

---

### Post by insanekat on 2011-05-10
Yeah I can do that, thanks.

---

### Post by jtarin on 2011-05-10
I should have added the easiest way to do that is search for the kernel you want to remove in Synaptic. It will update Grub for you.

---

### Post by insanekat on 2011-05-10
That actually made no difference. Oh well, I'll just keep selecting it manually until I can find a solution.

---

### Post by wilee-nilee on 2011-05-10
> **insanekat said:**
> That actually made no difference. Oh well, I'll just keep selecting it manually until I can find a solution.

I don't think you got the grub-legacy out.
sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   **/grub/menu.lst** /grub/grub.cfg /grub/core.img

I think you will be set if you do. Not sure here of the procedure though, generally we just purge all of grub both types, and reload grub-pc, and grub-common, and a boot partition isn't used.

So I think jtarin and I can get you working with easybcd but these anomalies, are a problem at least the dualing grubs.

Run the bootscript again, so we can see what is up if you want.  I would like to see you use easybcd as that's what's there, but if we can't get it working grub2 can be set up easily to work, I'm quite sure. I think easybcd will work though it needs to be seeing a healthy grub to work I suspect.

---

### Post by insanekat on 2011-05-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   100,018,974    99,609,375   7 HPFS/NTFS
/dev/sda3       1,432,502,272 1,464,936,447    32,434,176   7 HPFS/NTFS
/dev/sda4         100,020,222 1,432,500,223 1,332,480,002   5 Extended
/dev/sda5         100,020,224   100,995,071       974,848  83 Linux
/dev/sda6         100,997,120   120,526,847    19,529,728  83 Linux
/dev/sda7         120,528,896   124,432,383     3,903,488  82 Linux swap / Solaris
/dev/sda8         124,434,432 1,432,500,223 1,308,065,792  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        00D29D05D29D0058                       ntfs       SYSTEM                        
/dev/sda2        C81C96AE1C9696D2                       ntfs                                     
/dev/sda3        DC98B44C98B426C4                       ntfs       RECOVERY                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c5d098ae-dd08-4140-8804-6fd6fffecf64   ext2                                     
/dev/sda6        32a1a661-1bbd-41a8-a60d-a4a4067526e5   ext4                                     
/dev/sda7        9b87a354-5985-45a4-a441-537c81525bae   swap                                     
/dev/sda8        90d341f1-8355-4faa-b9c7-435cb2dd1249   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda8        /home                    ext4       (rw,commit=0)
/dev/sda5        /boot                    ext2       (rw)


============================= sda5/grub/menu.lst: =============================

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
# kopt=root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c5d098ae-dd08-4140-8804-6fd6fffecf64

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

title		Ubuntu 11.04, kernel 2.6.35-28-generic
uuid		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro quiet splash 
initrd		/initrd.img-2.6.35-28-generic

title		Ubuntu 11.04, kernel 2.6.35-28-generic (recovery mode)
uuid		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro  single
initrd		/initrd.img-2.6.35-28-generic

title		Chainload into GRUB 2
root		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/boot/grub/core.img

title		Ubuntu 11.04, memtest86+
uuid		c5d098ae-dd08-4140-8804-6fd6fffecf64
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

============================= sda5/grub/grub.cfg: =============================

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
set default="4"
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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 32a1a661-1bbd-41a8-a60d-a4a4067526e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
set locale_dir=($root)/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.38-8-generic-pae root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/vmlinuz-2.6.38-8-generic-pae root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.38-8-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/vmlinuz-2.6.35-28-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root c5d098ae-dd08-4140-8804-6fd6fffecf64
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 00D29D05D29D0058
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root C81C96AE1C9696D2
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root DC98B44C98B426C4
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

=================== sda5: Location of files loaded by Grub: ===================


  51.5GB: grub/core.img
  51.5GB: grub/grub.cfg
  51.5GB: grub/menu.lst
  51.2GB: initrd.img-2.6.35-22-generic
  51.2GB: initrd.img-2.6.35-28-generic
  51.2GB: vmlinuz-2.6.35-22-generic
  51.2GB: vmlinuz-2.6.35-28-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=32a1a661-1bbd-41a8-a60d-a4a4067526e5 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=c5d098ae-dd08-4140-8804-6fd6fffecf64 /boot           ext2    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=90d341f1-8355-4faa-b9c7-435cb2dd1249 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=9b87a354-5985-45a4-a441-537c81525bae none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 0e 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e0  0e 00 00 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5

00000000  eb 63 90 ff ff ff ff ff  ff ff ff ff ff ff ff ff  |.c..............|
00000010  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000050  ff ff ff ff ff ff ff ff  ff ff 00 80 a8 f4 fe 05  |................|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  ff ff ff ff ff ff ff ff  |...<.u..........|
000001c0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001f0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 55 aa  |..............U.|
00000200


```

---

### Post by jtarin on 2011-05-10
> **insanekat said:**
> That actually made no difference. Oh well, I'll just keep selecting it manually until I can find a solution.[Is this the screen your talking about?]("http://www.n00bsonubuntu.net/wp-content/uploads/ubuntu-grub2-boot-menu.jpg") List all your entries you see there.

---

### Post by insanekat on 2011-05-10
Yep!

Ubuntu with Linux 2.6.38-8
" (recovery mode)
Previous Linux Versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
" " (on /dev/sda2)
Windows Recovery Environment (loader) (on /dev/sda3)

Submenu of previous Linux Versions:
Ubuntu, with Linux 2.6.38-8
" (recovery mode)
Ubuntu, with Linux 2.6.35-28
" (recovery mode)
Ubuntu, with Linux 2.6.35-22
" (recovery mode)

---

### Post by jtarin on 2011-05-11
[Grub Customizer]("https://launchpad.net/~danielrichter2007/+archive/grub-customizer")

---

### Post by insanekat on 2011-05-11
Ha funnily enough I came across that when I was looking for a solution. I guess I just downloaded it but didn't install it and assumed it didn't work then moved on. Fail on my part! I will give this a try, thanks.

---

### Post by insanekat on 2011-05-11
Okay that didn't work, but I think I know why not, it's as you've been talking about most likely: When I get to the boot screen it says GRUB 1.99 at the top. 

Since I have 2 I have to remove one? Which one? Just in synaptic/terminal? And I assume that once I remove it that my laptop will just boot to the other one and problem solved, since these programs etc. appear to be editing that one, if that's possible.

---

### Post by oldfred on 2011-05-11
There have been some issues with upgrades. Grub 1.99 is the version with Natty. It has some internal changes that the gui tools now do not work and that may also effect EasyBCD. But I have not worked with EasyBCD, so I do not know. 

Having both grub legacy & grub2 almost is always a problem. And having a separate /boot complicated the repair process as you always have to mount it and some instructions do not tell you that as separate /boot is now rare for standard desktops. 

You also have to have a Natty liveCD to do repairs as any of the older versions will not work correctly with Natty.

I would try Supergrub first to get into system, if you cannot now.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Once booted you could uninstall grub & grub2 and cleanly reinstall grub2.

If Supergrub boot does not work:
Do you have a Natty liveCD? Then I would chroot into it, remove both grub & grub2 and cleanly reinstall grub2. I would also update system while in chroot. 

to reinstall grub2
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

### Post by insanekat on 2011-05-11
For reinstalling grub2, can I do this without backing up/booting from a liveCD?

---

### Post by oldfred on 2011-05-11
If you can boot into your system, even with older kernel then yes. You do need working Internet as it has to download latest grub2 files after you have deleted everything.

---

### Post by insanekat on 2011-05-11
That was generally successful in that I can now boot to the updated kernel, so thank you! However, now it boots straight to the grub boot loader screen instead of the EasyBCD menu of Ubuntu 11.04 and Windows 7. Is there a way to default back to that screen so that I can select Ubuntu 11.04 then select the kernel (or select Windows 7)?

---

### Post by oldfred on 2011-05-11
Does the windows boot from the grub menu work?

I do not know EasyBCD and if it works with 1.99. You can go to their site & see or maybe jtarin knows?

---

### Post by insanekat on 2011-05-11
When I boot to Windows from the grub menu, it goes to the EasyBCD menu.

---

### Post by oldfred on 2011-05-11
If the EasyBCD entry works to boot Ubuntu or can be updated to boot Ubuntu, you just need to reinstall a windows boot loader to boot the EasyBCD first.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by insanekat on 2011-05-11
```
bootrec.exe /fixboot
```
did nothing.
Do I absolutely have to boot from a CD? Because I can boot into Windows no problem.

---

### Post by jtarin on 2011-05-11
> **insanekat said:**
> ```
bootrec.exe /fixboot
```
did nothing.
Do I absolutely have to boot from a CD? Because I can boot into Windows no problem.
EasyBCD....IS.....your Windows boot menu. It has been expanded to include any other operating systems you may have on any other partitions that have "THEIR" native bootmanger installed to the partition of the OS.EasyBCD is also able restore the Windows MBR.(Vista/Win). Grub must be installed to the partition of the OS it is booting.....not the MBR of the disk. That is for EasyBCD to place its manager.
Oldfred's instructions for Grub are good....however it should be reinstalled not to /dev/sda....which is the MBR of the first disk. Each Grub should be reinstalled to its respective partition. /dev/sda should be reserved for the Windows boot manager/EasyBCD. I hope this is clear.

---

### Post by insanekat on 2011-05-11
Yep, thanks for all the help guys! Much appreciated!

---

### Post by wilee-nilee on 2011-05-11
So @jtarin is it restore the MS/easybcd boot with
```
bootrec.exe /fixmbr
```
From the MS recovery or install disc.

Or use the actual easybcd device to reload the mbr?

I'm going to mess with easybcd on summer break it would be nice to be more familiar.;)

---

### Post by jtarin on 2011-05-11
> **wilee-nilee said:**
> So @jtarin is it restore the MS/easybcd boot with
```
bootrec.exe /fixmbr
```
From the MS recovery or install disc.

Or use the actual easybcd device to reload the mbr?

I'm going to mess with easybcd on summer break it would be nice to be more familiar.;)You need to be in Windows to execute EasyBCD. It has the ability to restore and edit the MBR. "bootrec.exe /fixmbr" is a Recovery Disk function....seperate application.

---

### Post by wilee-nilee on 2011-05-12
> **jtarin said:**
> You need to be in Windows to execute EasyBCD. It has the ability to restore and edit the MBR. "bootrec.exe /fixmbr" is a Recovery Disk function....seperate application.

So what your saying is that restoring the MS bootloader, with a command Microsoft suggests for reloading the mbr, so you can boot straight to the Vista, then editing the MS boot with easybcd wont work? ;)

Grub has been fixed and the correct kernel now boots.

---

### Post by jtarin on 2011-05-12
> **wilee-nilee said:**
> So what your saying is that restoring the MS bootloader, with a command Microsoft suggests for reloading the mbr, so you can boot straight to the Vista, then editing the MS boot with easybcd wont work? ;)

Grub has been fixed and the correct kernel now boots.

I'm saying restoring thr MBR so it will boot into Windows is the only way to gain access to EasyBCD. It's a Windows environment tool.

---

### Post by wilee-nilee on 2011-05-12
> **jtarin said:**
> I'm saying restoring thr MBR so it will boot into Windows is the only way to gain access to EasyBCD. It's a Windows environment tool.

That is what I'm saying as well, I use that command to overwrite the grub in the mbr all the time and load the needed MS files to boot straight in.

I know there are other commands to do the same, but that command per MS is a standard to use to reload the MBR.
[http://support.microsoft.com/kb/919529](http://support.microsoft.com/kb/919529)
[http://neosmart.net/forums/showthread.php?t=8281](http://neosmart.net/forums/showthread.php?t=8281)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by wilee-nilee on 2011-05-12
This may help a bit.
[http://neosmart.net/forums/showthread.php?p=65340#post65340](http://neosmart.net/forums/showthread.php?p=65340#post65340)

---

### Post by insanekat on 2011-05-12
> **wilee-nilee said:**
> This may help a bit.
[http://neosmart.net/forums/showthread.php?p=65340#post65340](http://neosmart.net/forums/showthread.php?p=65340#post65340)
This is exactly what happened. Not necessarily a problem, it's only SLIGHTLY inconvenient if I want to boot Windows 7 directly, just have to go through some more menus. Booting Ubuntu is quicker now though, which is what I use by default, so it's almost more convenient this way haha. 

Thanks again :)

---

### Post by wilee-nilee on 2011-05-12
> **insanekat said:**
> This is exactly what happened. Not necessarily a problem, it's only SLIGHTLY inconvenient if I want to boot Windows 7 directly, just have to go through some more menus. Booting Ubuntu is quicker now though, which is what I use by default, so it's almost more convenient this way haha. 

Thanks again :)

No problem, with easybcd we don't see it much, and we or I rely on the very few people who do.

If your using the grub menu to get to the MS now and it's not going straight to Vista but the MS menu sill because of easybcd that can be fixed, so you go straight to Vista. I don't know the removal of the edit, but the easybcd forum will or the Windows 7 forum, if you don't get an answer here.;)

I have W7 and a bunch of linux installs when I choose W7 it goes straight to the login no menu's

---

### Post by zzmackan on 2011-05-12
Hi there, 

I don not manage to boot UBUNTU from my HDD. Get the message can not mount voulume...

Now I have tried to locate a solution on the forum but nothing seems to work. 

Can sombody please help me on this one.

Here the steps I have been taken so far>

  	 	 	 	 	 	  1.
 ubuntu@ubuntu:~$ sudo fdisk -l 
  
 Disk /dev/hda: 203.9 GB, 203928109056 bytes 
 255 heads, 63 sectors/track, 24792 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x38893888 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/hda1   *           1       24418   196137553+  83  Linux 
 /dev/hda2           24419       24792     3004155    5  Extended 
 /dev/hda5           24419       24792     3004123+  82  Linux swap / Solaris
 

 

 

 2.
 ubuntu@ubuntu:~$ sudo apt-get install ntfs-config 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 E: Couldn't find package ntfs-config 
 ubuntu@ubuntu:~$  
 

 3.
 ubuntu@ubuntu:~$ mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force 
 mount: only root can do that 
 ubuntu@ubuntu:~$

---

### Post by wilee-nilee on 2011-05-12
> **zzmackan said:**
> Hi there,

You will need to start your own thread, read the instructions carefully and use the code tags, this is very important.

So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Feel free to pm me **(if)** you start your own thread.

---

