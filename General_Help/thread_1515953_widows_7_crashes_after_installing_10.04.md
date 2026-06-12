---
title: "widows 7 crashes after installing 10.04"
date: 2010-06-23
forum: General Help
---

### Post by rahulerai on 2010-06-23
hiii all..
i just installed ubuntu 10.04 in my windows 7 s/m.(Dual boot)
ubuntu got installed without any problem.But now when i try to boot to windows,s/m get crashed on the way..i could just see the windows logo,but by then,blue screen crash occurs..
I dont have windows 7 DVD with me..is there any solutions??
any help is much appreciated.
:confused:

---

### Post by wilee-nilee on 2010-06-23
First just to confirm your setup run the bootscript in my signature and post it in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

IF your sure you have no corruption via malware, a virus or other areas, we can if your computer is setup correctly get you in to run a chkdsk, with a recovery cd, that is downloadable.

---

### Post by Mark Phelps on 2010-06-24
> **rahulerai said:**
> hiii all..
i just installed ubuntu 10.04 in my windows 7 s/m.(Dual boot)
ubuntu got installed without any problem.But now when i try to boot to windows,s/m get crashed on the way..i could just see the windows logo,but by then,blue screen crash occurs..
I dont have windows 7 DVD with me..is there any solutions??
any help is much appreciated.
:confused:

How did you install Ubuntu -- dual boot in its own partition, or inside MS Windows using Wubi?

IF the first, which is my guess, how did you make room for Ubuntu -- using the Win7 Disk Management utility (the right way) , or using the Ubuntu installer (the wrong way)?

If the second, you're going to have to repair the Win7 boot loader because you probably corrupted it using the Ubuntu installer.

---

### Post by wilee-nilee on 2010-06-24
> **Mark Phelps said:**
> How did you install Ubuntu -- dual boot in its own partition, or inside MS Windows using Wubi?

IF the first, which is my guess, how did you make room for Ubuntu -- using the Win7 Disk Management utility (the right way) , or using the Ubuntu installer (the wrong way)?

If the second, you're going to have to repair the Win7 boot loader because you probably corrupted it using the Ubuntu installer.

Good questions Mark that is why I default to the boot script it will tell us all we need to know, except how MS was resized, and if there are corrupted files in Windows.

I have gotten tired of 20 posts to get to the information that the script provides, and it is easy to make an error without full disclosure.:p

---

### Post by rahulerai on 2010-06-25
hey..the result of the bootscript is attachd here.
```
                                                                 
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       386021367 sectors, but according to the info from 
                       fdisk, it has 490879663 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       401,624       401,562  de Dell Utility
/dev/sda2             403,454    31,860,735    31,457,282   5 Extended
/dev/sda5             403,456    28,721,151    28,317,696  83 Linux
/dev/sda6          28,723,200    31,860,735     3,137,536  82 Linux swap / Solaris
/dev/sda3    *     31,860,736   134,260,735   102,400,000  42 SFS
/dev/sda4         134,260,736   625,140,399   490,879,664  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D9-070F                              vfat       DellUtility                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        28DACFA5DACF6E1E                       ntfs                                     
/dev/sda4        BE36A0E936A0A3BD                       ntfs                                     
/dev/sda5        54e8cb7a-0fa3-49dd-b9a3-2f9907246da6   ext4                                     
/dev/sda6        8d2a6e20-eba0-4fe9-b260-6e358c5405c6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		5

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
# kopt=root=UUID=54e8cb7a-0fa3-49dd-b9a3-2f9907246da6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=54e8cb7a-0fa3-49dd-b9a3-2f9907246da6

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=54e8cb7a-0fa3-49dd-b9a3-2f9907246da6 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=54e8cb7a-0fa3-49dd-b9a3-2f9907246da6 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
kernel		/boot/memtest86+.bin

title Windows 7
root (hd0,2)
savedefault
makeactive
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set 54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
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
search --no-floppy --fs-uuid --set 54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=54e8cb7a-0fa3-49dd-b9a3-2f9907246da6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=54e8cb7a-0fa3-49dd-b9a3-2f9907246da6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 54e8cb7a-0fa3-49dd-b9a3-2f9907246da6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 28dacfa5dacf6e1e
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
UUID=54e8cb7a-0fa3-49dd-b9a3-2f9907246da6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8d2a6e20-eba0-4fe9-b260-6e358c5405c6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   9.3GB: boot/grub/core.img
   9.3GB: boot/grub/grub.cfg
   3.1GB: boot/grub/menu.lst
   9.3GB: boot/grub/stage2
   9.9GB: boot/initrd.img-2.6.32-21-generic
   9.8GB: boot/vmlinuz-2.6.32-21-generic
   9.9GB: initrd.img
   9.8GB: vmlinuz
```




NO i didn't use ubuntu to create new partition..there was already a NTFS partition in my disk.i just deleted that and used it to instal ubuntu..
please help

---

