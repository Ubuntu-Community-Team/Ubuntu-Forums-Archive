---
title: "Windows 7 Boot option missing after installing Ubuntu"
date: 2011-01-12
forum: General Help
---

### Post by venuskalra on 2011-01-12
Was already having Windows 7 and ubuntu 10.10 and i installed ubuntu 11.04 with removable drive. Unfortunately, my windows 7 boot option is no more in menu. Please help me with this. 

This is how my menu.lst looks like..

```
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
# kopt=root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f1e7a04a-271d-46a2-9cd4-94a281cb871b

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

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)edited venus
uuid		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Chainload into GRUB 2
root		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by sikander3786 on 2011-01-12
Welcome to the forums :-)

Please boot Ubuntu and run bootinfoscript as per instructions here and post the results.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us more about your setup and thus we'll be able to advise accordingly.

---

### Post by venuskalra on 2011-01-12
Here it is.. result of bootinfoscript. what to do next?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 608636928 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 608637184 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 608660480 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 608636928 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 608660480 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda3          19,294,208   348,598,271   329,304,064   7 HPFS/NTFS
/dev/sda4         348,602,366   625,141,759   276,539,394   f W95 Ext d (LBA)
/dev/sda5         348,602,368   401,022,975    52,420,608   7 HPFS/NTFS
/dev/sda6         583,198,720   625,141,759    41,943,040  83 Linux
/dev/sda7         401,025,024   583,190,527   182,165,504  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda4: PTTYPE="dos" 
/dev/sda6        f1e7a04a-271d-46a2-9cd4-94a281cb871b   ext4                                     
/dev/sda7        c9d5d668-f5e3-46f6-a7a7-c255a52b9c37   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f1e7a04a-271d-46a2-9cd4-94a281cb871b

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

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)edited venus
uuid		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Chainload into GRUB 2
root		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		f1e7a04a-271d-46a2-9cd4-94a281cb871b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f1e7a04a-271d-46a2-9cd4-94a281cb871b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set f1e7a04a-271d-46a2-9cd4-94a281cb871b
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f1e7a04a-271d-46a2-9cd4-94a281cb871b
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f1e7a04a-271d-46a2-9cd4-94a281cb871b
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7? {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f1e7a04a-271d-46a2-9cd4-94a281cb871b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set f1e7a04a-271d-46a2-9cd4-94a281cb871b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.37-7-generic (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
	linux /boot/vmlinuz-2.6.37-7-generic root=UUID=c9d5d668-f5e3-46f6-a7a7-c255a52b9c37 ro quiet splash
	initrd /boot/initrd.img-2.6.37-7-generic
}
menuentry "Ubuntu, with Linux 2.6.37-7-generic (recovery mode) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
	linux /boot/vmlinuz-2.6.37-7-generic root=UUID=c9d5d668-f5e3-46f6-a7a7-c255a52b9c37 ro single
	initrd /boot/initrd.img-2.6.37-7-generic
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b /               ext4    errors=remount-ro 0       1

=================== sda6: Location of files loaded by Grub: ===================


 311.6GB: boot/grub/core.img
 316.3GB: boot/grub/grub.cfg
 316.4GB: boot/grub/menu.lst
 311.6GB: boot/grub/stage2
 300.0GB: boot/initrd.img-2.6.35-23-generic
 311.7GB: boot/vmlinuz-2.6.35-23-generic
 300.0GB: initrd.img
 311.7GB: vmlinuz

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
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
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.lst
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.37-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
	linux	/boot/vmlinuz-2.6.37-7-generic root=UUID=c9d5d668-f5e3-46f6-a7a7-c255a52b9c37 ro   quiet splash
	initrd	/boot/initrd.img-2.6.37-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
	echo	'Loading Linux 2.6.37-7-generic ...'
	linux	/boot/vmlinuz-2.6.37-7-generic root=UUID=c9d5d668-f5e3-46f6-a7a7-c255a52b9c37 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.37-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root c9d5d668-f5e3-46f6-a7a7-c255a52b9c37
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root f1e7a04a-271d-46a2-9cd4-94a281cb871b
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root f1e7a04a-271d-46a2-9cd4-94a281cb871b
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root f1e7a04a-271d-46a2-9cd4-94a281cb871b
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root f1e7a04a-271d-46a2-9cd4-94a281cb871b
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=f1e7a04a-271d-46a2-9cd4-94a281cb871b ro single
	initrd /boot/initrd.img-2.6.35-22-generic
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=c9d5d668-f5e3-46f6-a7a7-c255a52b9c37 /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 239.8GB: boot/grub/core.img
 231.2GB: boot/grub/grub.cfg
 231.3GB: boot/initrd.img-2.6.37-7-generic
 239.8GB: boot/vmlinuz-2.6.37-7-generic
 231.3GB: initrd.img
 239.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by sikander3786 on 2011-01-12
I suspect Windows 7 was supposed to be on sda1 and is no longer there. There might be a problem with partition tables and test disk might help recover your partition.

[https://help.ubuntu.com/community/DataRecovery#Testdisk](https://help.ubuntu.com/community/DataRecovery#Testdisk)

If Testdisk doesn't succeed and if there was some valuable data there, you might want to run photorec. It would change the file names but at least, would recover the data.

[https://help.ubuntu.com/community/DataRecovery#Photorec](https://help.ubuntu.com/community/DataRecovery#Photorec)

Regarding Grub, you've a mix of Grub Legacy and Grub2 whereas you need to have Grub2 installed. Follow this link to purge and re-install Grub.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

As it seems at present, it might need a bit of hard work to get things back in shape. If you can afford to, a re-install of everything might be the easy choice. But if there is some valuable data that wasn't backed up, you need to try all the recovery options.

Good Luck!

---

### Post by venuskalra on 2011-01-12
Need further help...

---

### Post by amsterdamharu on 2011-01-12
Do you have an option called "Chainload into GRUB 2"?
From there you should get the option called: [FONT=monospace]"Windows 7"[/FONT]
[FONT=monospace]
Allthough it looks like there is a syntax error there (/boot/grub/grub.cfg):
[/FONT]```
### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7[COLOR=Red]?[/COLOR] {
set root=(hd0,1)
chainloader +1
}
```[FONT=monospace]

When you're in grub menu (the first one) you can try the following:
Press c for command and type the following commands:
[/FONT]```
rootnoverify (hd0,1)
chainloader +1
boot
```That should boot you in Windows but better add it in /boot/grub/menu.lst

---

### Post by garvinrick4 on 2011-01-12
# These 2 links are for purging and reinstalling grub.
# The second for installing Windows boot manager.
You have choosen to keep grub-legacy as boot manager.
Read link #1 do you want to use grub2 since all you linux installs do?
# Get your Windows booting using 2nd link below and then purge and reinstall your choice
of grub.
# You seem to have had a lot going on trying to use different methods of install grub.
# I have no idea which windows version you are using shows no operating system.
# I suggest use 1st link and get yourself back together by purging all your grub's and starting over.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by sikander3786 on 2011-01-12
I highlight the basic problems here in Red.

```
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  [COLOR="Red"]Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 608636928 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''[/COLOR]
```

As you see, it is reporting that Grub 0.97 is installed in the boot sector of your partition, which doesn't need to be there. Instead, it just needs to be in the MBR of your drive. And each of your partition contains an instance of Grub 0.97. Purging Grub might cure this problem.

Secondly, Mounting of sda1, sda2, sda3 and sda5 failed. It is reporting Unknown Filesystem which doesn't sound good at all. Any of the data recovery options mentioned in above post might help.

---

