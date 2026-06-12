---
title: "Deleting 9.04 and not messing up grub and winxp"
date: 2010-05-23
forum: General Help
---

### Post by 45acp on 2010-05-23
I have two internal HD's. One with Jaunty(9.04)? the other with Xp. Since I installed Lucid on an external drive I no longer need Jaunty. Can I reformat the Jaunty drive to recover some disk space and not mess up grub with my (wife's) Xp?

---

### Post by kansasnoob on 2010-05-23
> **45acp said:**
> I have two internal HD's. One with Jaunty(9.04)? the other with Xp. Since I installed Lucid on an external drive I no longer need Jaunty. Can I reformat the Jaunty drive to recover some disk space and not mess up grub with my (wife's) Xp?

No. Assuming you did install Lucid's grub to the mbr of the external (and not the internal) you should be depending on Jaunty's grub to boot the internal drives right now, and on Lucid's grub2 only when the external is plugged in.

In order for us to see what bootloader is installed where we need you to post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mikewhatever on 2010-05-23
When installing Lucid, have you kept the default grub location? If so, there shouldn't be a problem, and in case there is, it's fairly easy to fix both grub and the Windows bootloader..

---

### Post by 45acp on 2010-05-23
When I installed Lucid I install only to the external drive. I actually disconnected the Win and Jaunty internal drives to install Lucid to the external so as not to overwrite anything by mistake. I believe grub is installed to on the first Windows drive. The grub menu only shows jaunty and WinXp. I hope this helps.

---

### Post by kansasnoob on 2010-05-23
The only way we can actually see for sure is if you post the output of the Boot Info Script, but it sounds like you'll need to restore the Windows MBR to the internal drive after removing Jaunty. Or possibly just change the disc boot priority in BIOS.

All we can do is guess without seeing the requested output.

---

### Post by 45acp on 2010-05-23
Here are the results of the boot script.

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdh1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdh1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      8,530,515   234,436,544   225,906,030   7 HPFS/NTFS
/dev/sda2                  63     8,530,514     8,530,452   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   151,010,999   151,010,937  83 Linux
/dev/sdb2         151,011,000   156,296,384     5,285,385   5 Extended
/dev/sdb5         151,011,063   156,296,384     5,285,322  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   307,335,167   307,333,120  83 Linux
/dev/sdc2         307,337,214   312,580,095     5,242,882   5 Extended
/dev/sdc5         307,337,216   312,580,095     5,242,880  82 Linux swap / Solaris


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63     7,855,784     7,855,722   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/truecrypt1 a92940a7-ed3a-454d-9603-356c8e665e6d   ext3                                     
/dev/sda1        AC0CB9A20CB9684A                       ntfs       Windows                       
/dev/sda2        423B-2BDF                              vfat       RECOVERY                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c6479ee4-4a1c-4580-a21b-27fd0f108b7c   ext3                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e4bed8af-f021-4dcd-8058-3504712aafb1   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0a562dc7-ee2a-4916-894a-8eea3d510f4e   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        f5b833b9-65e5-4698-a5ab-654c088c4b4a   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdh1        2A6F-3B51                              vfat                                     
/dev/sdh         4B05-266D                              vfat                                     
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
truecrypt1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/mapper/truecrypt1 /media/truecrypt1        ext3       (rw)
/dev/sdh1        /media/2A6F-3B51         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


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
# kopt=root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 9.04, kernel 2.6.28-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 9.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c6479ee4-4a1c-4580-a21b-27fd0f108b7c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=e4bed8af-f021-4dcd-8058-3504712aafb1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  19.6GB: boot/grub/menu.lst
  19.4GB: boot/grub/stage2
  19.4GB: boot/initrd.img-2.6.24-21-generic
  19.4GB: boot/initrd.img-2.6.24-21-generic.bak
  19.5GB: boot/initrd.img-2.6.27-11-generic
  19.5GB: boot/initrd.img-2.6.28-13-generic
  19.6GB: boot/initrd.img-2.6.28-15-generic
  19.6GB: boot/initrd.img-2.6.28-18-generic
  19.5GB: boot/vmlinuz-2.6.24-21-generic
  19.5GB: boot/vmlinuz-2.6.27-11-generic
  19.5GB: boot/vmlinuz-2.6.28-13-generic
  19.5GB: boot/vmlinuz-2.6.28-15-generic
  19.5GB: boot/vmlinuz-2.6.28-18-generic
  19.6GB: initrd.img
  19.6GB: initrd.img.old
  19.5GB: vmlinuz
  19.5GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0a562dc7-ee2a-4916-894a-8eea3d510f4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0a562dc7-ee2a-4916-894a-8eea3d510f4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0a562dc7-ee2a-4916-894a-8eea3d510f4e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=0a562dc7-ee2a-4916-894a-8eea3d510f4e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0a562dc7-ee2a-4916-894a-8eea3d510f4e
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0a562dc7-ee2a-4916-894a-8eea3d510f4e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f5b833b9-65e5-4698-a5ab-654c088c4b4a none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


  55.9GB: boot/grub/core.img
 120.5GB: boot/grub/grub.cfg
  55.9GB: boot/initrd.img-2.6.32-21-generic
  60.1GB: boot/initrd.img-2.6.32-22-generic
  55.9GB: boot/vmlinuz-2.6.32-21-generic
  55.9GB: boot/vmlinuz-2.6.32-22-generic
  60.1GB: initrd.img
  55.9GB: initrd.img.old
  55.9GB: vmlinuz
  55.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdh

00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 08 06 00  |.X.mkdosfs......|
00000010  02 00 00 00 00 f8 00 00  3e 00 7c 00 00 00 00 00  |........>.|.....|
00000020  7f fa 77 00 f0 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 03 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 6d 26 05 4b 00  00 00 00 00 00 00 00 00  |..)m&.K.........|
00000050  00 00 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |..FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 0d 0a 00 00 00 00  00 00 00 00 00 00 00 00  |sk..............|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  61 9b 05 00 00 00 00 01  |........a.......|
000001c0  01 00 0b fe 7f e8 3f 00  00 00 6a de 77 00 00 00  |......?...j.w...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  d2 3b 44 dd 5b 5b bf bb  24 71 08 77 8d 35 e7 ee  |.;D.[[..$q.w.5..|
00000010  44 02 15 77 c6 6f fb 2d  7f f6 ec da 2d 8a 9b 15  |D..w.o.-....-...|
00000020  70 04 08 67 db 9e 0a f0  bb c3 07 72 2b 28 a4 1c  |p..g.......r+(..|
00000030  d9 59 2e be 33 cd 8d d0  a1 39 f7 c6 04 cd ef 87  |.Y..3....9......|
00000040  72 8b cc fa 3f a2 48 18  02 88 55 71 25 a9 13 2d  |r...?.H...Uq%..-|
00000050  be b7 98 bb 6b d4 f7 e3  d9 35 a2 66 d4 15 c8 35  |....k....5.f...5|
00000060  86 dc 5e 86 df f9 9b da  0c 64 39 78 44 fd 7e aa  |..^......d9xD.~.|
00000070  b8 ae 2f 4d df 71 79 32  08 59 b1 52 c8 10 3b 5e  |../M.qy2.Y.R..;^|
00000080  5a 98 8c 5b 77 ae fc 82  09 57 fd 85 16 18 f4 e7  |Z..[w....W......|
00000090  cd 15 0e 61 89 8c 50 d2  09 57 a8 31 6a 3e 32 3a  |...a..P..W.1j>2:|
000000a0  a6 55 e1 2a 22 06 1b b0  85 f1 ad ed b1 ba a1 61  |.U.*"..........a|
000000b0  33 97 88 06 e7 9d fe 48  ff 38 cc 94 d2 36 a4 01  |3......H.8...6..|
000000c0  ae db 88 93 79 2a 0a ac  46 bc 48 ac 5d 70 cb c0  |....y*..F.H.]p..|
000000d0  b5 bc b3 0c de db 7b f4  d7 42 e7 b3 9d c6 f1 59  |......{..B.....Y|
000000e0  80 63 08 43 94 23 06 69  34 ef 9a 5e 8c 76 f0 c4  |.c.C.#.i4..^.v..|
000000f0  65 d1 c7 8d a7 e6 c6 d6  10 a5 69 23 9d bd 11 d4  |e.........i#....|
00000100  ed ea 36 8d fb 3b 7c 9d  c9 42 c5 58 ce 9c 93 4f  |..6..;|..B.X...O|
00000110  6e 47 08 9a 78 6e 5a 58  ae e1 c1 a9 9b 70 c4 47  |nG..xnZX.....p.G|
00000120  98 e4 9a b9 c9 4a 52 f9  af 48 63 f8 c0 75 18 2b  |.....JR..Hc..u.+|
00000130  fd 4a fc c2 39 b2 c4 20  32 85 62 16 2f bc 36 e0  |.J..9.. 2.b./.6.|
00000140  a8 75 60 d4 de ae e3 cc  37 37 db 3d 3e 95 55 06  |.u`.....77.=>.U.|
00000150  ce 99 1c 58 02 8e 29 db  3b 47 6b 39 94 35 f5 f8  |...X..).;Gk9.5..|
00000160  b8 24 ca e1 88 8a 4d d6  e4 b7 8d ce d4 64 45 da  |.$....M......dE.|
00000170  31 68 b4 3e 88 80 35 4e  c7 c6 3a 06 ac f2 05 ba  |1h.>..5N..:.....|
00000180  23 5b 5f 5a d5 fa cc 47  42 f7 9b 60 f8 c2 48 f5  |#[_Z...GB..`..H.|
00000190  ad 44 7d d1 c0 57 4f 27  08 b6 cb 2d 0f e9 93 9e  |.D}..WO'...-....|
000001a0  5f 31 38 ab 7a ad a6 30  06 f3 73 7b 7c 96 55 d2  |_18.z..0..s{|.U.|
000001b0  9b 43 e1 98 19 3a af 1b  f5 59 b1 97 c6 0d 00 fe  |.C...:...Y......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 50 00 00 00  |............P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

Not sure what a lot of this means

---

### Post by kansasnoob on 2010-05-23
OK, /dev/sdc is clearly the external and all looks fine:

> sdc1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 

We can see that Lucid's grub2 is on it's MBR:

> Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in
partition #1 for /boot/grub.

As far as the internals, /dev/sda is the 120.0 GB drive and houses Win XP, and /dev/sdb is 80.0 GB and houses Jaunty:

> sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

> sdb1: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab

But both /dev/sda and /dev/sdb have a legacy grub mbr:

> => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
=> Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

Now what I don't know is if the two internals are a mixture of SATA and IDE, or possibly both IDE connected to one cable, but I'd assume that /dev/sda (the 120GB Windows drive) is the first boot priority in BIOS so you'll need to restore the Windows MBR either using an XP disc:

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

Or you can do so using Ubuntu and running in terminal:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Note, if you run that from your installed Lucid I always like to remove the package lilo when I'm done so it doesn't mess with the grub 2 configuration at some point, so just:

```
sudo apt-get remove lilo
```

Then if your BIOS settings are correct you should be able to boot Windows after removing Jaunty with the external drive disconnected and boot Lucid only when the external is connected.

If you run "sudo update-grub" in Lucid, Windows should also be added to it's boot menu without harm. But I'd be derelict if I didn't warn you of this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

During updates at some point you'll undoubtedly be asked where to install grub. In your case it's /dev/sdc and ONLY /dev/sdc :)

---

### Post by 45acp on 2010-05-23
Thanks for the help. The way I understood it was that grub was installed to sda (windows drive) when I installed Jaunty to sdb. If I reformatted sdb then grub on sda just would just not find jaunty (from the grub boot menu) while leaving the windows grub menu entry unaffected. This would not be a problem if the window grub entry would still work. Lucid on the external is booted from the bios menu not the grub menu. It is entirely separate.

---

### Post by kansasnoob on 2010-05-23
> **45acp said:**
> Thanks for the help. The way I understood it was that grub was installed to sda (windows drive) when I installed Jaunty to sdb. If I reformatted sdb then grub on sda just would just not find jaunty (from the grub boot menu) while leaving the windows grub menu entry unaffected. This would not be a problem if the window grub entry would still work. Lucid on the external is booted from the bios menu not the grub menu. It is entirely separate.

It does not work that way, parts of grub exist within the operating system:

> Grub 0.97 is installed in the MBR of /dev/sda and [B][COLOR="Red"]looks on boot drive #2
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR][/B]

Once stage2 and menu.lst are gone grub "hunts" and returns an error :)

---

### Post by 45acp on 2010-05-23
That what I was afraid of. Thanks

---

