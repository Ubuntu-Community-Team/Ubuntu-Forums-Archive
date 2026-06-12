---
title: "GRUB2 error: no such device: grub rescue UUID doesn't exist"
date: 2010-09-29
forum: General Help
---

### Post by tj77 on 2010-09-29
I've seen different threads on the "error: no such device" when booting using Grub2 but none that address my situation.  I have a single boot, ubuntu installation where the boot drive is (hd1).  (hd0) is a data drive.

The UUID after the "no such device" error is not a drive on my system at all.  Here are the steps I've taken so far.  

I can boot manually from the grub rescue command line.  

I can list my devices using fdisk and blckid to verify that the UUID from the error is not present.  

I've reinstalled grub using "grub install /dev/sdb".  

I've updated grub using "grub update".  

And, I've tried reinstalling using "grub install --recheck /dev/sdb".  The error remains.

Advice?

---

### Post by philinux on 2010-09-29
Run the bootinfoscript and post back the results.txt file.

[http://www.google.com/m/url?channel=bm&client=ms-palm-webOS&ei=cpCjTIC4F9C4jAeitc3VAQ&q=http://sourceforge.net/projects/bootinfoscript/&ved=0CA0QFjAA&usg=AFQjCNEQ0Nvo6-CcO4B6Nw6ft3FTapKY_g](http://www.google.com/m/url?channel=bm&client=ms-palm-webOS&ei=cpCjTIC4F9C4jAeitc3VAQ&q=http://sourceforge.net/projects/bootinfoscript/&ved=0CA0QFjAA&usg=AFQjCNEQ0Nvo6-CcO4B6Nw6ft3FTapKY_g)

---

### Post by tj77 on 2010-09-30
Results from bootinfo are attached (as a tarball.  It seems the results are too long to upload as a .txt).  The only error I can see is that there's an unknown bootloader on /dev/sdb2.  

I should say that before I started receiving this error during boot, I attempted to install Windows 7 on VirtualBox.  The installation failed, though, I expect that all Windows 7 files would be written to the virtual drive created by VirtualBox.  Perhaps that isn't true.

Thanks for the help.
TJ

---

### Post by trbooth on 2010-10-22
Any update? I may have a similar problem.

---

### Post by tj77 on 2010-10-22
I still don't have it fixed and have heard from no one on an answer.

---

### Post by Quackers on 2010-10-22
This is your boot script between CODE tags

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 139464887 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   468,407,204   468,407,142  83 Linux
/dev/sdb2         468,407,266   488,279,609    19,872,344   5 Extended
/dev/sdb5         468,407,268   488,279,609    19,872,342  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56F4F1CFF4F1B0FB                       ntfs       Research                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        923c9380-8548-468e-8045-313d4687118d   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        b435ea4f-76bd-4831-994c-d9205ed0a1e2   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        e05ee578-aaec-4076-8b9f-2060881b61bb   xfs                                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda1        /mnt/research            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /mnt/lidar               xfs        (rw)
/dev/sr0         /media/cdrom0            udf        (ro,nosuid,nodev,utf8,user=toddjobe)


=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=923c9380-8548-468e-8045-313d4687118d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=923c9380-8548-468e-8045-313d4687118d

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.27-11-generic (recovery mode)
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Chainload into GRUB 2
root		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		923c9380-8548-468e-8045-313d4687118d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
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
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	echo	'Loading Linux 2.6.28-16-generic ...'
	linux	/boot/vmlinuz-2.6.28-16-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux	/boot/vmlinuz-2.6.27-11-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro   quiet splash
	initrd	/boot/initrd.img-2.6.27-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	echo	'Loading Linux 2.6.27-11-generic ...'
	linux	/boot/vmlinuz-2.6.27-11-generic root=UUID=923c9380-8548-468e-8045-313d4687118d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.27-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 923c9380-8548-468e-8045-313d4687118d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=923c9380-8548-468e-8045-313d4687118d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=b435ea4f-76bd-4831-994c-d9205ed0a1e2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1	/mnt/research ntfs-3g	    gid=1004 	  0	  0
/dev/sdc1	/mnt/lidar 	xfs	    exec  0	  0
//152.2.51.156/nclidar          /mnt/floodplainLidar      smbfs   username=toddjobe@ad.unc.edu,noauto,user,ro,exec        0       0
//152.2.51.156/Moody_Lab          /mnt/moody_lab      smbfs   username=toddjobe@ad.unc.edu,noauto,user,ro,exec        0       0
//152.2.24.199/nasa/NASA          /mnt/nasa      smbfs   username=toddjobe@ad.unc.edu,noauto,user,ro,exec        0       0           



=================== sdb1: Location of files loaded by Grub: ===================


 123.4GB: boot/grub/core.img
  62.6GB: boot/grub/grub.cfg
  62.6GB: boot/grub/menu.lst
  71.4GB: boot/grub/stage2
 130.3GB: boot/initrd.img-2.6.27-11-generic
  89.0GB: boot/initrd.img-2.6.28-16-generic
 142.0GB: boot/initrd.img-2.6.31-21-generic
  79.9GB: boot/initrd.img-2.6.32-22-generic
  62.6GB: boot/initrd.img-2.6.32-23-generic
  78.8GB: boot/initrd.img-2.6.32-24-generic
 121.9GB: boot/vmlinuz-2.6.27-11-generic
 128.7GB: boot/vmlinuz-2.6.28-16-generic
 121.9GB: boot/vmlinuz-2.6.31-21-generic
  71.2GB: boot/vmlinuz-2.6.32-22-generic
 123.0GB: boot/vmlinuz-2.6.32-23-generic
  78.7GB: boot/vmlinuz-2.6.32-24-generic
  78.8GB: initrd.img
  62.6GB: initrd.img.old
  78.7GB: vmlinuz
 123.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  90 7e 3e 40 69 7d 71 70  77 74 70 72 74 71 71 69  |.~>@i}qpwtprtqqi|
00000010  6b 6b 69 7a 7b 78 74 6e  6f 70 66 67 74 70 75 60  |kkiz{xtnopfgtpu`|
00000020  6c 75 6a 69 7a 87 86 80  7a 73 6b 6d 6d 6b 6a 67  |lujiz...zskmmkjg|
00000030  74 8d 81 78 63 75 8b 86  7d 77 77 71 5e 64 7f 8b  |t..xcu..}wwq^d..|
00000040  77 71 6c 84 85 78 6d 6e  5f 6a 78 8a 86 71 69 64  |wql..xmn_jx..qid|
00000050  6b 61 58 5e 61 90 9b 61  50 4e 41 32 54 87 98 68  |kaX^a..aPNA2T..h|
00000060  4a 5f 4a 54 5e 5b 6a 56  5d 66 5a 60 5f 62 61 51  |J_JT^[jV]fZ`_baQ|
00000070  52 4b 4b 54 4f 53 56 55  5a 57 5a 5d 59 5d 6c 67  |RKKTOSVUZWZ]Y]lg|
00000080  5d 61 5f 76 72 62 65 6b  58 60 5d 55 58 5e 56 57  |]a_vrbekX`]UX^VW|
00000090  5a 59 4e 63 64 4b 52 5f  5f 62 66 68 5d 5f 61 6c  |ZYNcdKR__bfh]_al|
000000a0  71 78 78 7b 77 72 72 76  75 77 77 78 79 79 7a 71  |qxx{wrrvuwwxyyzq|
000000b0  64 55 67 89 98 8a 87 87  8a 8c 8a 7c 79 7a 7b 87  |dUg........|yz{.|
000000c0  80 6f 5b 77 75 76 82 67  57 72 7a 70 6e 63 46 57  |.o[wuv.gWrzpncFW|
000000d0  67 6b 5f 69 63 72 66 6a  6d 80 7e 7f 63 74 66 6a  |gk_icrfjm.~.ctfj|
000000e0  73 62 6b 79 80 7f 75 73  69 69 78 7c 84 75 75 84  |sbky..usiix|.uu.|
000000f0  7e 7d 7e 80 7d 88 8a 8d  7a 53 70 77 71 4f 6c 76  |~}~.}...zSpwqOlv|
00000100  65 60 69 73 6b 67 67 71  6e 66 6f 72 6e 77 6e 7c  |e`iskggqnfornwn||
00000110  70 7a 74 75 6b 76 73 7b  7f 6e 6c 7a 76 80 7a 78  |pztukvs{.nlzv.zx|
00000120  69 6d 7b 7a 62 6a 70 72  77 73 6a 6b 74 76 72 70  |im{zbjprwsjktvrp|
00000130  6b 63 70 76 64 6c 60 4f  47 44 5d 52 3c 3c 46 6d  |kcpvdl`OGD]R<<Fm|
00000140  66 58 64 4d 41 57 64 57  5b a9 c2 c2 77 56 5f 68  |fXdMAWdW[...wV_h|
00000150  6c 6d 73 78 6d 69 68 6b  6b 6d bd 8b 74 72 66 5a  |lmsxmihkkm..trfZ|
00000160  77 b2 6a 63 62 63 67 61  4c 56 6c 6f 5c 5a 5b 55  |w.jcbcgaLVlo\Z[U|
00000170  5d 66 5e 50 51 5f 50 5b  4d 5f 4e 62 5a 5e 64 4c  |]f^PQ_P[M_NbZ^dL|
00000180  35 25 24 3d 64 6c 69 5f  6e 69 68 65 5f 6c 5d 5e  |5%$=dli_nihe_l]^|
00000190  7f 86 6a 5e 89 6f 68 6b  6f 74 7e 78 5b 4f 7a 7a  |..j^.ohkot~x[Ozz|
000001a0  75 77 68 5c 6a 5b 35 49  5a 41 49 3d 5d 7a 63 75  |uwh\j[5IZAI=]zcu|
000001b0  7f 7d 72 67 75 60 69 5d  5d 62 6d 68 4d 4d 00 fe  |.}rgu`i]]bmhMM..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 56 3a 2f 01 00 00  |..........V:/...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde 
```

Why is grub legacy installed in sdb1? It seems you have re-installed grub and not grub2.

---

### Post by oldfred on 2010-10-22
If you are for sure booting the 250GB drive in BIOS (as the entry in hd0 does look wrong), then you need to chroot into your system and totally uninstall grub & grub2 and cleanly reinstall grub2.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by tj77 on 2010-12-09
I have worked around the problem.  I did a couple of purges and reinstalls of both grub and grub2, but the problem was not fixed.  I think the issue is that there is a Master Boot Record defined on my first hard drive (/dev/hda). I'm not clear how I did that, but it's there.  No matter how I fixed grub on my boot drive (/dev/hdb), the bios would still try to boot /dev/hda first because of the MBR.  So, I just switched the boot order in the bios.  Then grub2 on /dev/hdb worked great.  Now I just need to figure out how completely remove the MBR on /dev/hda and have it show up as not bootable.  

Thanks for all the help.

---

