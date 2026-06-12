---
title: "GRUB error 15, after repartitioning"
date: 2011-04-16
forum: General Help
---

### Post by sshh on 2011-04-16
After I made a new partition with **Gparted **and installed **Backtrack** on it, I keep getting 
error 15 **("Error 15: File not found"). **
I can't boot Ubuntu (aforementioned error) but windows is fine. 
I can get access to my files with BT or the cd, the files are there. 
I also don't have access to the home folder, it's encrypted. 

Any way to make everything return to normal and use ubuntu again?

---

### Post by oldfred on 2011-04-16
Error 15 is often conflicts between grub legacy & grub2. Did you let backtrack install its bootloader? Or are you not using UUIDs and changed partition numbers?

To see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by sshh on 2011-04-16
Thank you for your reply. 

Yes, I used Backtrack's bootloader (left the default options).
Also, the ubuntu kernels do not show as they used to, but look rather like commands (full of ""'s and --option --option things).
Windows, which used to be 
1. Windows loader
2. Windows loader (recovery mode) 
    now shows up as 
1.Windows 
2.Windows. 
(sic).


Now the main part (RESULTS.txt from the script): 

```
===

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /grldr /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD /grldr

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

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hda: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc5fcbd5f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   369,999,871   369,999,809   7 HPFS/NTFS
/dev/sda2         460,471,095   484,095,999    23,624,905   7 HPFS/NTFS
/dev/sda3         370,523,160   460,471,094    89,947,935   5 Extended
/dev/sda5         397,848,576   460,470,271    62,621,696  83 Linux
/dev/sda6         370,523,286   396,580,589    26,057,304  83 Linux
/dev/sda7         396,580,653   397,833,659     1,253,007  82 Linux swap / Solaris
/dev/sda4         370,009,080   370,523,159       514,080  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8dacbce

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda                                                iso9660    sysrcd-2.1.0                  
/dev/sda1        F6B4D42CB4D3ED5D                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sda4        9ac607f3-5daf-41cd-93fc-1f88558987a1   ext2       btr4r3                        
/dev/sda5        f672ba56-6e6e-4773-a6a7-8d3da85be903   ext4                                     
/dev/sda6        52acce6b-13bd-46d7-8575-5b919e655ef1   ext3                                     
/dev/sda7        9c51038d-f3f8-41e2-9aa3-b21c28c432b9   swap                                     
/dev/sdb1        44C054C0C054BA3E                       ntfs       SH external drv               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


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
search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f672ba56-6e6e-4773-a6a7-8d3da85be903
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set f6b4d42cb4d3ed5d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
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
UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=54a7dad0-f285-481d-bb52-59ae93560a2b none            swap    sw              0       0
/mnt/512Mb.swap  none  swap  sw  0 0


=================== sda5: Location of files loaded by Grub: ===================


 227.5GB: boot/grub/core.img
 227.4GB: boot/grub/grub.cfg
 210.5GB: boot/initrd.img-2.6.35-22-generic
 223.7GB: boot/initrd.img-2.6.35-25-generic
 234.2GB: boot/initrd.img-2.6.35-27-generic
 234.4GB: boot/initrd.img-2.6.35-28-generic
 227.5GB: boot/vmlinuz-2.6.35-22-generic
 227.5GB: boot/vmlinuz-2.6.35-25-generic
 227.8GB: boot/vmlinuz-2.6.35-27-generic
 227.8GB: boot/vmlinuz-2.6.35-28-generic
 234.4GB: initrd.img
 234.2GB: initrd.img.old
 227.8GB: vmlinuz
 227.8GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=52acce6b-13bd-46d7-8575-5b919e655ef1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=52acce6b-13bd-46d7-8575-5b919e655ef1

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=52acce6b-13bd-46d7-8575-5b919e655ef1/boot/grub/splash.xpm.gz

title		BackTrack 4 R2, kernel 2.6.35.8
uuid		52acce6b-13bd-46d7-8575-5b919e655ef1
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=52acce6b-13bd-46d7-8575-5b919e655ef1 ro quiet splash 
initrd		/boot/initrd.img-2.6.35.8
quiet

title		BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid		52acce6b-13bd-46d7-8575-5b919e655ef1
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=52acce6b-13bd-46d7-8575-5b919e655ef1 ro  single
initrd		/boot/initrd.img-2.6.35.8

title		BackTrack 4 R2, memtest86+
uuid		52acce6b-13bd-46d7-8575-5b919e655ef1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
initrd		/boot/initrd.img-2.6.35-28-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
initrd		/boot/initrd.img-2.6.35-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
initrd		/boot/initrd.img-2.6.35-25-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=f672ba56-6e6e-4773-a6a7-8d3da85be903 ro single 
initrd		/boot/initrd.img-2.6.35-22-generic
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=52acce6b-13bd-46d7-8575-5b919e655ef1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=9c51038d-f3f8-41e2-9aa3-b21c28c432b9 none            swap    sw              0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 193.8GB: boot/grub/menu.lst
 193.8GB: boot/grub/stage2
 193.5GB: boot/initrd.img-2.6.35.8
 193.5GB: boot/vmlinuz-2.6.35.8
 193.5GB: initrd.img
 193.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi



```.


I'm not using wubi, if that helps.

---

### Post by oldfred on 2011-04-16
Do not know what version of grub legacy Backtrack is using. Ubuntu modified their version of old grub with 9.04 to be able to use ext4 partitions.

I would just reinstall Ubuntu's grub2 boot loader to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by sshh on 2011-04-16
I tried to do it, but I got
```
sudo grub-install --recheck --root-directory=/mnt/sda5/ /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
[B]The file /mnt/sda5//boot/grub/stage1 not read correctly.
[/B]
```

Is it corrupted? I'm sure the file exists in the place where I mounted it. 
Here's the content, I doubt it will help:
```
ëH^Ð^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^$
öÂ^À^O^Äê^@é^Í^@¾^E|ÆDÿ^@f1À^Èð@f^ÉD^D1Ò^ÈÊÁâ^B^Èè^Èô@^ÉD^H1À^ÈÐÀè^Bf^É^Df¡D|f1$
f1Òf÷t^D^ÈT^K^ÉD^L;D^H}<^ÊT^MÀâ^F^ÊL
þÁ^HÑ^Êl^LZ^Êt^K»^@p^ÎÃ1Û¸^A^BÍ^Sr*^ÌÃ^Î^FH|`^^¹^@^A^ÎÛ1ö1ÿüó¥^_aÿ&B|¾^Å}è@^@ë^$





```

---

### Post by oldfred on 2011-04-16
Did you do the mount & the install first?

You have to run commands I posted in order. The ones without the # or comment.

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

You only need the reinstall if the above gives errors. And the update is run after rebooting.

---

### Post by sshh on 2011-04-17
I put the commands exactly. 
Even after copy/pasting, I still get the error. 

I tried to so something, but now I can't even load backtrack. Now I'm working from live usb. 

All the files are there, from all the OS's. I'm sure something can be done.
Reinstalling isn't a problem, but I just don't want to do it. There's all the stuff I've tweaked for months.

And the Home folder is encrypted, so I can't copy anything from it. But I know the pass and the passphrase. But still I'm sure there's a solution.

---

### Post by sshh on 2011-04-17
Figured it out. 

I logged in my Ubuntu system via System Rescue CD, then resetting grub via```
 apt-get remove grub-pc grub-common grub
``` and ```
apt-get install grub-pc grub-common 
```

---

