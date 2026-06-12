---
title: "Grub wont correctly recognise OS on second drive"
date: 2010-03-27
forum: General Help
---

### Post by glubbdrubb on 2010-03-27
I have 2 internal harddrives. 

I installed Vista on sdb1 and later Ubuntu on sda1.

When I boot up, I am given  choice of OS's to boot into. That worked fine until I formatted sdb1 and installed Windows 7.

Now when I boot, I am given the exact same options as before, and when I select the the old "Vista" Menu item, it gives me an error that it can not find some long serial number. The number is not my drive serial number. That number is completely different. 

I can still boot into Ubuntu with out a problem.

Now, in order for me to boot into windows, I have change the BIOS boot order. That is obviously not ideal.

---

### Post by drs305 on 2010-03-27
Please run this script so we can see what Grub(2) is looking at. Once you have run the script and are ready to paste, press the **#** in the post's menu and copy the results between the "code" tags.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by glubbdrubb on 2010-03-27
sdc1 and sdd1 are non bootable storage drives. Would it not be easier if I just uploaded the results as a text file?

Any how, here you are:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf249b0d6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   484,488,269   484,488,207  83 Linux
/dev/sda2         484,488,270   488,392,064     3,903,795  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x46ee9a1d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ccef4

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4089 MB, 4089445376 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7987198 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031493

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63     7,984,304     7,984,242   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e9906709-ab20-4f30-970f-49071c3d97d9   ext4                                     
/dev/sda2        1ae10820-736d-4702-b8fe-4c63e77b6d46   swap                                     
/dev/sdb1        9EB015BBB0159ABB                       ntfs                                     
/dev/sdc1        3468589168585428                       ntfs       1TB                           
/dev/sdd1        49A1-1B04                              vfat       GLUBBDRUBB                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1        /media/GLUBBDRUBB        vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e9906709-ab20-4f30-970f-49071c3d97d9

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f400e77500e73d6c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                       0  0  
# / was on /dev/sda1 during installation
UUID=e9906709-ab20-4f30-970f-49071c3d97d9  /              ext4         errors=remount-ro                              0  1  
# swap was on /dev/sda5 during installation
UUID=5616b4de-a32f-46c9-8b25-32254b8217d8  none           swap         sw                                             0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                          0  0  

/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,users,umask=000,user,uid=victor  0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                                       0  0  
/dev/sdc1                                  /media/sdc1    ntfs         defaults                                       0  0  

=================== sda1: Location of files loaded by Grub: ===================


  10.5GB: boot/grub/core.img
   1.0GB: boot/grub/grub.cfg
   3.5GB: boot/grub/menu.lst
   2.0GB: boot/initrd.img-2.6.31-14-generic
   7.3GB: boot/initrd.img-2.6.31-15-generic
  82.0GB: boot/initrd.img-2.6.31-16-generic
   1.6GB: boot/initrd.img-2.6.31-17-generic
  39.7GB: boot/initrd.img-2.6.31-19-generic
   9.5GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.4GB: boot/vmlinuz-2.6.31-15-generic
   2.1GB: boot/vmlinuz-2.6.31-16-generic
   9.2GB: boot/vmlinuz-2.6.31-17-generic
   1.5GB: boot/vmlinuz-2.6.31-19-generic
   1.3GB: boot/vmlinuz-2.6.31-20-generic
   9.5GB: initrd.img
  39.7GB: initrd.img.old
   1.3GB: vmlinuz
   1.5GB: vmlinuz.old
```

That is one hell of a script you've got there.


f400e77500e73d6c is the serial number that the error says grub cant find.

---

### Post by oldfred on 2010-03-27
When you reinstalled windows the partition got a new UUID. So you need to run 

sudo update-grub

That should find and reset the entry to see the correct new UUID for the windows partition. You also still have the menu.lst from an old grub legacy boot that you do not have anymore.

---

### Post by glubbdrubb on 2010-03-27
It did not work. Here are the latest results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf249b0d6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   484,488,269   484,488,207  83 Linux
/dev/sda2         484,488,270   488,392,064     3,903,795  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x46ee9a1d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ccef4

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4089 MB, 4089445376 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7987198 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031493

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63     7,984,304     7,984,242   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e9906709-ab20-4f30-970f-49071c3d97d9   ext4                                     
/dev/sda2        1ae10820-736d-4702-b8fe-4c63e77b6d46   swap                                     
/dev/sdb1        9EB015BBB0159ABB                       ntfs                                     
/dev/sdc1        3468589168585428                       ntfs       1TB                           
/dev/sdd1        49A1-1B04                              vfat       GLUBBDRUBB                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdd1        /media/GLUBBDRUBB        vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1        /media/1TB               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e9906709-ab20-4f30-970f-49071c3d97d9

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		e9906709-ab20-4f30-970f-49071c3d97d9
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e9906709-ab20-4f30-970f-49071c3d97d9
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e9906709-ab20-4f30-970f-49071c3d97d9 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f400e77500e73d6c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                       0  0  
# / was on /dev/sda1 during installation
UUID=e9906709-ab20-4f30-970f-49071c3d97d9  /              ext4         errors=remount-ro                              0  1  
# swap was on /dev/sda5 during installation
UUID=5616b4de-a32f-46c9-8b25-32254b8217d8  none           swap         sw                                             0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                          0  0  

/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,users,umask=000,user,uid=victor  0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                                       0  0  
/dev/sdc1                                  /media/sdc1    ntfs         defaults                                       0  0  

=================== sda1: Location of files loaded by Grub: ===================


  10.5GB: boot/grub/core.img
   1.0GB: boot/grub/grub.cfg
   4.0GB: boot/grub/menu.lst
   2.0GB: boot/initrd.img-2.6.31-14-generic
   7.3GB: boot/initrd.img-2.6.31-15-generic
  82.0GB: boot/initrd.img-2.6.31-16-generic
   1.6GB: boot/initrd.img-2.6.31-17-generic
  39.7GB: boot/initrd.img-2.6.31-19-generic
   9.5GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
   1.4GB: boot/vmlinuz-2.6.31-15-generic
   2.1GB: boot/vmlinuz-2.6.31-16-generic
   9.2GB: boot/vmlinuz-2.6.31-17-generic
   1.5GB: boot/vmlinuz-2.6.31-19-generic
   1.3GB: boot/vmlinuz-2.6.31-20-generic
   9.5GB: initrd.img
  39.7GB: initrd.img.old
   1.3GB: vmlinuz
   1.5GB: vmlinuz.old
```

---

### Post by oldfred on 2010-03-27
Grub2 is almost always good at finding working windows. Only when windows will not boot because of missing files does it not find it. I  wonder if old grub is interfering?

You can uninstall both grub and grub2 (grub-pc) and reinstall grub2.
purge old and reinstall new to sdb
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sdb
sudo update-grub

The other choice is to add a manual entry to 40_custom to boot:

You add entries to this
/etc/grub.d/40_custom

menuentry "Microsoft Windows 7 (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 9EB015BBB0159ABB
    drivemap -s (hd0) ${root}
    chainloader +1
}

The only thing I am not sure of with windows on hd1 is the drivemap. It may be
 drivemap -s (hd1) ${root}

You could put two entries in an see which works or try one then if not change hd0 to hd1

---

### Post by glubbdrubb on 2010-03-27
Sorry I took so long to get back to you, but removing the old version of grub and reinstalling grub2 did the job. So it worked!

Thanks a lot.

---

