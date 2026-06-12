---
title: "Messed up my MBR -- bricked computer"
date: 2010-11-19
forum: General Help
---

### Post by Djalmahal on 2010-11-19
My hard drive was a bit of a mess, too many partitions, so I tried to clean it up and have messed up the MBR.

When I boot it up now it can't find anything, because (I believe) I deleted GRUB.

Here is the layout 

/dev/sda1 fat 32 Windows Recovery
/dev/sda2 ntfs   Windows
/dev/sda3
  /dev/sda5 ext4 was formerly a working Ubuntu 10.04 install
  /unallocated (I deleted this partition today)
  /dev/sda6 linux-swap
  /dev/sda7 ext4 /home partition
  /unallocated (formerly sda8 and where GRUB was, I had 10.10 RC candidate installed and deleted it today not knowing it would cause such problems)
  /dev/sda8 linux-swap for 10.10 RC

I looked it up on the forums

sudo grub
find /boot/grub/stage1

comes up with Error 15:file not found

as well as another forum with

buntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda: Not found or not a block device.
root@ubuntu:/# 

So this didn't work. Currently running 1004 of a USB.

So please help me, cause the USB-booting is all I can do at the moment

Andreas

---

### Post by lmarmisa on 2010-11-19
Try these commands:

```

sudo bash
mount /dev/sda5 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
exit
reboot

```

---

### Post by Djalmahal on 2010-11-19
root@ubuntu:/# grub-install /dev/sda
/dev/sda does not have any corresponding BIOS drive.
root@ubuntu:/#

---

### Post by wilee-nilee on 2010-11-19
This is why I asked you questions in your thread on the subject of resizing.

Boot a live Ubuntu cd click on the bootscript link in my signature, follow the instructions. paste the text from the generated file to a reply,** but click on the # in the reply window and paste the text between the code tags.**

You have put the cart before the horse in trying to do things in a haphazard method I think, it happens no big deal but post the script.

---

### Post by lmarmisa on 2010-11-19
Try:

```

sudo bash
mount /dev/sda5 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
grub-install --recheck /dev/sda
exit
reboot

```

---

### Post by wojox on 2010-11-19
Just reinstall Grub2 [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Djalmahal on 2010-11-19
Ok, I didn't know how to get the code tags before, now I do


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #10 for (,msdos10)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    40,965,749    40,963,702  1c Hidden W95 FAT32 (LBA)
/dev/sda2          40,965,750   257,666,534   216,700,785   7 HPFS/NTFS
/dev/sda3         257,666,596   976,773,119   719,106,524   5 Extended
/dev/sda5         257,666,598   281,109,957    23,443,360  83 Linux
/dev/sda6         296,736,678   306,504,134     9,767,457  82 Linux swap / Solaris
/dev/sda7         306,504,198   949,235,979   642,731,782  83 Linux
/dev/sda8         975,521,792   976,773,119     1,251,328  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2003 MB, 2003795968 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        782800C42800837C                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        80134c5c-543d-4d3c-b591-89e6747bcfed   ext4                                     
/dev/sda6        b9855183-d9f0-4488-8a50-b4a0dcc44eb4   swap                                     
/dev/sda7        9364e5df-9bc3-493b-b74b-5bd9ef59042e   ext4                                     
/dev/sda8        10dae2b7-3096-431f-8355-d82971cbb101   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0A73-81A9                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     ext4       (rw)
/dev             /mnt/dev                 none       (rw,bind)


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
# kopt=root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=80134c5c-543d-4d3c-b591-89e6747bcfed

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
uuid		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		80134c5c-543d-4d3c-b591-89e6747bcfed
kernel		/boot/memtest86+.bin

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
search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
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
search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3c98-ac5d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 782800c42800837c
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set fe414275-97a7-4b36-aca1-f8798bae51b4
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe414275-97a7-4b36-aca1-f8798bae51b4 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set fe414275-97a7-4b36-aca1-f8798bae51b4
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=fe414275-97a7-4b36-aca1-f8798bae51b4 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu maverick (development branch) (10.10) (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set cbbca64e-d5cc-44fc-854a-4b2ef7de426f
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda9
	initrd /boot/initrd.img-2.6.35-22-generic
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
UUID=80134c5c-543d-4d3c-b591-89e6747bcfed /               ext4    errors=remount-ro 0       1
/dev/sda7       /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b9855183-d9f0-4488-8a50-b4a0dcc44eb4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 140.8GB: boot/grub/core.img
 139.3GB: boot/grub/grub.cfg
 140.3GB: boot/grub/menu.lst
 142.5GB: boot/initrd.img-2.6.32-21-generic
 143.0GB: boot/initrd.img-2.6.32-22-generic
 140.5GB: boot/initrd.img-2.6.32-24-generic
 140.8GB: boot/vmlinuz-2.6.32-21-generic
 134.1GB: boot/vmlinuz-2.6.32-22-generic
 142.5GB: boot/vmlinuz-2.6.32-24-generic
 140.5GB: initrd.img
 143.0GB: initrd.img.old
 142.5GB: vmlinuz
 134.1GB: vmlinuz.old
```

---

### Post by Djalmahal on 2010-11-19
Ok, the
 ```
grub-install --recheck /dev/sda

```

worked insofar as my 10.04 install is again bootable and recognized, only the Windows partition is not showing up in the GRUB menu.

---

### Post by wilee-nilee on 2010-11-19
sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/**grub/menu.lst** /boot/**grub/grub.cfg** /etc/fstab 
                       /boot/grub/core.img

You have grub-legacy and grub2 installed this doesn't work, and grub is pointed at partition 10 which doesn't exist.
```
 Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
   ** partition #10** for (,msdos10)/boot/grub.

```
 So take a look at this tutorial on purging both grubs and installing grub2 correctly.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by lmarmisa on 2010-11-19
> **Djalmahal said:**
> Ok, the
 ```
grub-install --recheck /dev/sda

```worked insofar as my 10.04 install is again bootable and recognized, only the Windows partition is not showing up in the GRUB menu.

Ok. Try this command now:

```

sudo update-grub

```

and check if Windows is detected.

---

### Post by wilee-nilee on 2010-11-19
> **lmarmisa said:**
> Ok. Try this command now:

```

sudo update-grub

```

and check if Windows is detected.

Read my post and the script please.;) It may have booted but there are both grubs showing in the script. This will be a big problem if history repeats itself of this sort of circumstances.

---

### Post by Djalmahal on 2010-11-19
OK, will look it the thread up, thanks
sudo update-grub doesn't show windows

---

### Post by wilee-nilee on 2010-11-19
> **Djalmahal said:**
> OK, will look it the thread up, thanks
sudo update-grub doesn't show windows

We are all a team here and it is easy to just give advice, but as we see in this situation that didn't work.;)

When it comes to booting problems that script will save your, well you know what I mean, it also has a lot of other relevant info.

---

### Post by Djalmahal on 2010-11-19
SO now in GRUB i also have the option to load in bootchainloader, though it only result in an error.

Here are the contents of /boot/grub/grub.cfg

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
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
search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro  splash vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=80134c5c-543d-4d3c-b591-89e6747bcfed ro single  splash vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 80134c5c-543d-4d3c-b591-89e6747bcfed
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3c98-ac5d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 782800c42800837c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

It recognizes the Windows partition in the end of the file, is the "chainloader +1" responsible for the error, and does the HOWTO:Purge and Reinstall GRUB Tutorial fix it?

---

### Post by Rubi1200 on 2010-11-19
As wilee-nilee already mentioned, having a mixture of GRUB-legacy and GRUB2 can, and does, cause problems.

In any event, as wilee-nilee also pointed out, GRUB was pointing to a partition that appears not to exist.

I highly recommend you follow the advice posted and purge and reinstall GRUB to the MBR of sda.

If you need help with the commands, let us know.

Thanks.

---

### Post by wilee-nilee on 2010-11-19
> **Rubi1200 said:**
> As wilee-nilee already mentioned, having a mixture of GRUB-legacy and GRUB2 can, and does, cause problems.

In any event, as wilee-nilee also pointed out, GRUB was pointing to a partition that appears not to exist.

I highly recommend you follow the advice posted and purge and reinstall GRUB to the MBR of sda.

If you need help with the commands, let us know.

Thanks.

Thanks for your input Rubi1200.

Edit: OP if you still have problems after running more commands post the script again that is how we are best able to get to what might be any problems.

---

