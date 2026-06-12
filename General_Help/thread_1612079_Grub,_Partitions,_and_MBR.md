---
title: "Grub, Partitions, and MBR"
date: 2010-11-02
forum: General Help
---

### Post by jstarr20052005 on 2010-11-02
I am not sure how I have gotten into this mess, but maybe a little help from someone more experienced may help:

this is my setup:
 when I startup my computer, the computer loads grub off of an external drive. if the drive is not plugged in, I get an error (which I will post after check it again) that will not allow me to boot. although I should still be able to boot a live-cd or live-usb

when I do boot I get grub version 1.98+20100804-5ubuntu3
 I have these option to boot
 
 Ubuntu
 ubuntu recovery,
 memtest (memtest86+)
 memtest (memtest86+, serial console 115200) 
 windows recovery environment (loader) (on /dev/sda1)
 windows(loader) (on /dev/sda2)

now ubuntu boots perfect
ubuntu recovery boots perfect
memtest works fine
windows recovery boots regular windows
windows boots windows recovery

if I choose to boot windows (under windows recovery) i get a Windows boot menu with windows or ubuntu, from a previously installed version of ubuntu that wouldn't work after i tried the 10.10 beta, :( ,but windows works fine from there.

what would be preferred 
one boot screen from startup that would allow me to choose from windows, or ubuntu. with ubuntu installed on the external drive. 

one last ? why is the external drive not recognized in windows?, you can see it in device manager, but it doesn't mount a file system...

---

### Post by Rubi1200 on 2010-11-03
Hi,
in  order to give us a better overview of what is where, please boot the computer with a LiveCD and post the results of the boot-script linked at the bottom of my post.

Wrap the text with the # tag when posting or generate the tag and paste the text between.

Thanks.

---

### Post by jstarr20052005 on 2010-11-10
this is what i get,
  #                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbe809154

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   463,218,209   463,218,147   7 HPFS/NTFS
/dev/sda2         463,218,210   488,392,064    25,173,855   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f0a87

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,849,447     7,849,386   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072932864 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c1abe

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   606,713,855   606,711,808  83 Linux
/dev/sdc2         606,715,902   625,141,759    18,425,858   5 Extended
/dev/sdc5         606,715,904   625,141,759    18,425,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       db64d9b0-715b-4516-b9f4-ab9f30f17b41   ext3                                     
/dev/sda1        3E18FB4F18FB0525                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY                   
/dev/sdb1        7EFA-773D                              vfat                                     
/dev/sdc1        e22a6976-9e50-46e4-a61a-686ca4cab2dd   ext4                                     
/dev/sdc5        c153b13b-a8af-4d40-a231-899eb4c7fcc9   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/e22a6976-9e50-46e4-a61a-686ca4cab2dd ext4       (rw,nosuid,nodev,uhelper=devkit)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e22a6976-9e50-46e4-a61a-686ca4cab2dd
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set e22a6976-9e50-46e4-a61a-686ca4cab2dd
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e22a6976-9e50-46e4-a61a-686ca4cab2dd
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e22a6976-9e50-46e4-a61a-686ca4cab2dd ro  vga=775 splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e22a6976-9e50-46e4-a61a-686ca4cab2dd
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e22a6976-9e50-46e4-a61a-686ca4cab2dd ro single  vga=775 splash
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e22a6976-9e50-46e4-a61a-686ca4cab2dd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set e22a6976-9e50-46e4-a61a-686ca4cab2dd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 3e18fb4f18fb0525
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=c153b13b-a8af-4d40-a231-899eb4c7fcc9 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


 307.2GB: boot/grub/core.img
 281.6GB: boot/grub/grub.cfg
  71.2GB: boot/initrd.img-2.6.35-22-generic
 307.2GB: boot/vmlinuz-2.6.35-22-generic
  71.2GB: initrd.img
 307.2GB: vmlinuz
#

---

