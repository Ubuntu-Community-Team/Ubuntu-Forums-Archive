---
title: "Ubuntu, Win7, Intel 915 Mobo, Dual boot"
date: 2010-02-18
forum: General Help
---

### Post by TransitMan on 2010-02-18
I have the above named motherboard, with 4 SATA drives, 2 DVD/RW drives (IDE) and Ubuntu on one drive and Win7 on another.
I have Googled, I have searched and looked at and even implimented some of the recommendations for Dual Booting with no success.
Does anyone have another thought on this issue or should I just forget it and move on.

Also, sde and sdh do not have Windows installed on them. They are just back-up data drives formatted in NTFS.

And for reference material, below is a copy of the boot-info script.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf
 => No known boot loader is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005c0f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,482,874    20,482,812  83 Linux
/dev/sda2          20,482,875    28,884,869     8,401,995  82 Linux swap / Solaris
/dev/sda3          28,884,870 1,250,258,624 1,221,373,755   5 Extended
/dev/sda5          28,884,933    42,202,754    13,317,822  83 Linux
/dev/sda6          42,202,818    55,520,639    13,317,822  83 Linux
/dev/sda7          55,520,703    86,236,919    30,716,217  83 Linux
/dev/sda8          86,236,983   147,669,479    61,432,497  83 Linux
/dev/sda9         147,669,543   209,102,039    61,432,497  83 Linux
/dev/sda10        209,102,103 1,250,258,624 1,041,156,522  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c7399

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,049    82,524,159    82,522,111   7 HPFS/NTFS
/dev/sdb2          82,525,905   312,576,704   230,050,800   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000d76e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ee2b

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfd37cde

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c5a85

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3d8e295

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8be2f02b

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       adb175b1-8649-45db-9fad-5e84a15a0fb9   ext3                                     
/dev/sda1        6d1bfbc3-888e-4ca6-8501-70d63e2e8e30   ext3                                     
/dev/sda2        7edc45e4-8761-4652-854a-6e851fa41f19   swap                                     
/dev/sda5        1c51a2c6-68c7-4549-83e9-2074588b8459   ext3                                     
/dev/sda6        3dbd30d1-06ce-4073-aff0-f0ed692d29d9   ext3                                     
/dev/sda7        1948dca1-6098-45d5-99b5-b8e19e4ee265   ext3                                     
/dev/sda8        b4f91d6c-07e5-47ac-a924-110a2865804c   ext3                                     
/dev/sda9        0816d3e8-21c6-4a30-af58-7d97551bc205   ext3                                     
/dev/sdb1        1C38598138595B3A                       ntfs                                     
/dev/sdb2        7A4E6FDE13A91E1F                       ntfs                                     
/dev/sdc1        086D9AE2572224B2                       ntfs       Music                         
/dev/sdd1        55047F3A047AC801                       ntfs       VIDEO_1                       
/dev/sde1        1F16536218265DAC                       ntfs       Downloads                     
/dev/sdf1        60F8FE0A72A8E0A0                       ntfs       MOVIES3                       
/dev/sdg1        5616F38466B95C63                       ntfs       Music_BU                      
/dev/sdh1        2B4297031FDA5907                       ntfs       Movies2                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw)
/dev/sdd1        /media/VIDEO_1           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/Music             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda10       /home                    ext3       (rw)
/dev/sda5        /opt                     ext3       (rw)
/dev/sda6        /var                     ext3       (rw)
/dev/sda7        /tmp                     ext3       (rw)
/dev/sda8        /usr                     ext3       (rw)
/dev/sda9        /usr/local               ext3       (rw)
/dev/sdg1        /media/Music_BU          fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sde1        /media/Downloads         fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdh1        /media/Movies2           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdf1        /media/MOVIES3           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
# kopt=root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30

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
uuid		6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title	  	Windows 7 (x86)
root       	(hd,0)
map        	(hd0) (hd2)
map        	(hd2) (hd0)
chainloader 	+1

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set b4f91d6c-07e5-47ac-a924-110a2865804c
if loadfont /share/grub/unicode.pf2 ; then
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6d1bfbc3-888e-4ca6-8501-70d63e2e8e30
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1c38598138595b3a
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# Entry for /dev/sda1 :
UUID=6d1bfbc3-888e-4ca6-8501-70d63e2e8e30 / ext3 defaults 0 1
# Entry for /dev/sda10 :
UUID=adb175b1-8649-45db-9fad-5e84a15a0fb9 /home ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=7edc45e4-8761-4652-854a-6e851fa41f19 swap swap sw 0 0
# Entry for /dev/sda6 :
UUID=3dbd30d1-06ce-4073-aff0-f0ed692d29d9 /var ext3 defaults 0 2
# Entry for /dev/sda7 :
UUID=1948dca1-6098-45d5-99b5-b8e19e4ee265 /tmp ext3 defaults 0 2
# Entry for /dev/sda8 :
UUID=b4f91d6c-07e5-47ac-a924-110a2865804c /usr ext3 defaults 0 2
# Entry for /dev/sda5 :
UUID=1c51a2c6-68c7-4549-83e9-2074588b8459 /opt ext3 defaults 0 2
# Entry for /dev/sda9 :
UUID=0816d3e8-21c6-4a30-af58-7d97551bc205 /usr/local ext3 defaults 0 2
# Entry for /dev/sdd1 :
UUID=55047F3A047AC801 /media/VIDEO_1 ntfs-3g defaults 0 0
# Entry for /dev/sdc1 :
UUID=086D9AE2572224B2 /media/Music ntfs-3g defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/core.img
   3.1GB: boot/grub/grub.cfg
   3.1GB: boot/grub/menu.lst
   3.1GB: boot/grub/stage2
   3.2GB: boot/initrd.img-2.6.31-14-generic
   3.1GB: boot/initrd.img-2.6.31-20-generic
   3.1GB: boot/vmlinuz-2.6.31-14-generic
   3.1GB: boot/vmlinuz-2.6.31-20-generic
   3.1GB: initrd.img
   3.2GB: initrd.img.old
   3.1GB: vmlinuz
   3.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdg

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  95 e2 d8 c3 00 00 00 01  |................|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 8a a1 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdi 
```

---

### Post by meierfra. on 2010-02-18
What  exactly is your problem? 
I'm guessing that you can boot Ubuntu but not Windows. Is that correct?  
What error message do you get?
Or do you boot directly into Windows?

You also have  mixture of Grub legacy and Grub 2.  I think you will be better off switching  completely to Grub 2. To get started on that, post the output of 
 
```
grub-install -v
```

---

### Post by TransitMan on 2010-02-18
I boot into Ubuntu/Grub and scroll to my Windows 7 install, click on it and the after a few moments, the screen goes black and the system reboots.
If I try it from Windows7 boot menu (after having installed EasyBCD), I get the same black screen and reboot.

Output of ```
grub-install -v
grub-install (GNU GRUB 1.97~beta4)
```

---

### Post by meierfra. on 2010-02-18
Sounds like a Windows problem. But before we start trouble shooting Windows, try this

```
sudo grub-install --recheck /dev/sda
```

Then reboot and   choose Win 7 at the Grub menu.
Reboot again. But this time set your bios to boot from your 160GB Windows drive,

Report any error messages you got.

---

### Post by TransitMan on 2010-02-18
From ```
sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
(hd5)	/dev/sdf
(hd6)	/dev/sdg
(hd7)	/dev/sdh

```

Rebooted from Grub menu, choose Windows 7, again black screen and reboot.
Went and changed boot disc in BIOS and booted into Windows, no issues.

NOTE * I had issues with Win7 booting as I had gotten a NTLDR missing, with my Win7 disc, fixed the mbr on Win7. Since then, no issues in booting to Win7 with a BIOS hard drive switch. Also, I had this issue several days ago, and got it resolved. Still wanting to fix this dual-boot issue, though. Don't want to play with the BIOS to do it.

EDIT1 * The SATA layout for the motherboard is 0/2 and 1/3 if this helps. Not sure why it is, but if this sheds light on the problem, maybe a swap of SATA 2 to SATA1?

---

### Post by meierfra. on 2010-02-18
> Since then, no issues in booting to Win7 with a BIOS hard drive switch. A
O.K. Then it is not a  Windows, but a Grub problem.

 Your Win 7 entry in grub.cfg does not have a "drivemap" line. But some installation of Win 7 require it.  So lets create a custom entry and see whether it helps:

```
gksudo gedit /etc/grub.d/40_custom
```
add this to the end of the file

```
menuentry "Windows 7 (custom)" {
	insmod ntfs
	set root=(hd1,1)
        search --no-floppy --fs-uuid --set 1c38598138595b3a
        drivemap -s (hd0) ${root}
	chainloader +1
}
```

Save the file. Then back in the terminal:

```
sudo update-grub
```


Reboot and try  the new "Window 7(custom)" entry.

If you still can't boot into Win 7 from the grub menu:  Report any error message. Also run the boot info script again and post the new RESULTS.txt(it might be called RESULTS1.txt).

---

### Post by TransitMan on 2010-02-18
Custom entry did not work.
Moved Win7 from SATA 2 to SATA 1. Win7 boot fine if that drive is selected.
Results from boot-info-script
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
 => No boot loader is installed in the MBR of /dev/sdf
 => No known boot loader is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #63 on boot drive #1
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005c0f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,482,874    20,482,812  83 Linux
/dev/sda2    *     20,482,875    28,884,869     8,401,995  82 Linux swap / Solaris
/dev/sda3          28,884,870 1,250,258,624 1,221,373,755   5 Extended
/dev/sda5          28,884,933    42,202,754    13,317,822  83 Linux
/dev/sda6          42,202,818    55,520,639    13,317,822  83 Linux
/dev/sda7          55,520,703    86,236,919    30,716,217  83 Linux
/dev/sda8          86,236,983   147,669,479    61,432,497  83 Linux
/dev/sda9         147,669,543   209,102,039    61,432,497  83 Linux
/dev/sda10        209,102,103 1,250,258,624 1,041,156,522  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000d76e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c7399

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,049    82,524,159    82,522,111   7 HPFS/NTFS
/dev/sdc2    *     82,525,905   312,576,704   230,050,800   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ee2b

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfd37cde

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c5a85

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3d8e295

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8be2f02b

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       adb175b1-8649-45db-9fad-5e84a15a0fb9   ext3                                     
/dev/sda1        ef7a3f32-3d63-4ad7-8afa-c829353fec91   ext3                                     
/dev/sda2        7edc45e4-8761-4652-854a-6e851fa41f19   swap                                     
/dev/sda5        ad2bd143-1189-43a4-80f1-dd0a455ba862   ext3                                     
/dev/sda6        36cbc61e-46cd-4526-af6c-60ee58ff80bc   ext3                                     
/dev/sda7        1948dca1-6098-45d5-99b5-b8e19e4ee265   ext3                                     
/dev/sda8        7f0b75f7-befd-44b7-9108-6f117d2c4ba0   ext3                                     
/dev/sda9        0816d3e8-21c6-4a30-af58-7d97551bc205   ext3                                     
/dev/sdb1        086D9AE2572224B2                       ntfs       Music                         
/dev/sdc1        1C38598138595B3A                       ntfs                                     
/dev/sdc2        7A4E6FDE13A91E1F                       ntfs                                     
/dev/sdd1        55047F3A047AC801                       ntfs       VIDEO_1                       
/dev/sde1        1F16536218265DAC                       ntfs       Downloads                     
/dev/sdf1        60F8FE0A72A8E0A0                       ntfs       MOVIES3                       
/dev/sdg1        5616F38466B95C63                       ntfs       Music_BU                      
/dev/sdh1        2B4297031FDA5907                       ntfs       Movies2                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro)
/dev/sda10       /home                    ext3       (rw)
/dev/sdc1        /media/Music             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/Win7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1        /media/VIDEO_1           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc2        /media/Windows7          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /opt                     ext3       (rw)
/dev/sda6        /var                     ext3       (rw)
/dev/sda7        /tmp                     ext3       (rw)
/dev/sda8        /usr                     ext3       (rw)
/dev/sda9        /usr/local               ext3       (rw)
/dev/sdg1        /media/Music_BU          fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sde1        /media/Downloads         fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdh1        /media/Movies2           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdf1        /media/MOVIES3           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
# kopt=root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ef7a3f32-3d63-4ad7-8afa-c829353fec91

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
uuid		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		ef7a3f32-3d63-4ad7-8afa-c829353fec91
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Windows 7 Home Premium (Loader)
root	 	(hd1,1)
savedefault
makeactive
chainloader 	+1



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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 7f0b75f7-befd-44b7-9108-6f117d2c4ba0
if loadfont /share/grub/unicode.pf2 ; then
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
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set ef7a3f32-3d63-4ad7-8afa-c829353fec91
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ef7a3f32-3d63-4ad7-8afa-c829353fec91
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ef7a3f32-3d63-4ad7-8afa-c829353fec91
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ef7a3f32-3d63-4ad7-8afa-c829353fec91
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ef7a3f32-3d63-4ad7-8afa-c829353fec91
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ef7a3f32-3d63-4ad7-8afa-c829353fec91
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ef7a3f32-3d63-4ad7-8afa-c829353fec91
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 ro single 
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=ef7a3f32-3d63-4ad7-8afa-c829353fec91 / ext3 errors=remount-ro 0 1
# Entry for /dev/sda10 :
UUID=adb175b1-8649-45db-9fad-5e84a15a0fb9 /home ext3 defaults 0 2
# Entry for /dev/sda5 :
UUID=ad2bd143-1189-43a4-80f1-dd0a455ba862 /opt ext3 defaults 0 2
# Entry for /dev/sda7 :
UUID=1948dca1-6098-45d5-99b5-b8e19e4ee265 /tmp ext3 defaults 0 2
# Entry for /dev/sda8 :
UUID=7f0b75f7-befd-44b7-9108-6f117d2c4ba0 /usr ext3 defaults 0 2
# Entry for /dev/sda9 :
UUID=0816d3e8-21c6-4a30-af58-7d97551bc205 /usr/local ext3 defaults 0 2
# Entry for /dev/sda6 :
UUID=36cbc61e-46cd-4526-af6c-60ee58ff80bc /var ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=7edc45e4-8761-4652-854a-6e851fa41f19 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc1 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Win7 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdd1 /media/VIDEO_1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb2 /media/sdb2 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdc2 /media/Windows7 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda1: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
   6.4GB: boot/grub/grub.cfg
   6.5GB: boot/grub/menu.lst
   6.5GB: boot/grub/stage2
   6.5GB: boot/initrd.img-2.6.31-14-generic
   6.4GB: boot/initrd.img-2.6.31-19-generic
   6.4GB: boot/initrd.img-2.6.31-20-generic
   6.4GB: boot/vmlinuz-2.6.31-14-generic
   6.5GB: boot/vmlinuz-2.6.31-19-generic
   6.5GB: boot/vmlinuz-2.6.31-20-generic
   6.4GB: initrd.img
   6.4GB: initrd.img.old
   6.5GB: vmlinuz
   6.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdg

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  95 e2 d8 c3 00 00 00 01  |................|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 8a a1 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdi 
```

---

### Post by meierfra. on 2010-02-18
> Custom entry did not work.
More information please. Did the new entry show up on the Grub? Did you get the same "black screen and reboot"?

According to RESULTS.txt,  you don't have any Windows Entry on the Grub Menu. Also the scripts 30_os-prober and 40_custom did not run. Did you disable them?

Could you post the output  of

```
ls -l /etc/grub.d
```

---

### Post by TransitMan on 2010-02-18
From ```
ls -l /etc/grub.d

total 36
-rwxr-xr-x 1 root root 3296 2009-10-16 12:30 00_header
-rwxr-xr-x 1 root root 1154 2010-01-10 05:54 05_debian_theme
-rwxr-xr-x 1 root root 3778 2009-10-16 12:30 10_linux
-rwxr-xr-x 1 root root  772 2009-10-23 12:11 20_memtest86+
-rw-r--r-- 1 root root 5467 2009-12-07 18:08 30_os-prober
-rw-r--r-- 1 root root  390 2010-02-18 16:34 40_custom
-rw-r--r-- 1 root root  483 2009-10-16 12:30 README

```

Custom entry gave the same results, black screen and reboot.

---

### Post by meierfra. on 2010-02-18
> -rw-r--r-- 1 root root 5467 2009-12-07 18:08 30_os-prober
-rw-r--r-- 1 root root  390 2010-02-18 16:34 40_custom

Did you  change the executable bit on  those two files?  Why?  One of the reason I asked for the new RESULTS.txt was so that I could see the new menu entry you created. But since  you disabled  40_custom it longer appears in "grub.cfg".


Anyway, let's see what happens if  you install grub to the MBR of the windows drive:

```
sudo grub-install --recheck /dev/sdc
sudo chmod u+x /etc/grub.d/30_os-prober
sudo update-grub
```

Then reboot from the Windows drive.

---

### Post by TransitMan on 2010-02-18
Ok, completed the above and came up with booting from the sdc drive into Ubuntu but not Windows7.

Now where do we go?

---

### Post by meierfra. on 2010-02-18
Lets restore the MBR of /dev/sdc so that you can boot into Windows again:



```
sudo apt-get install lilo
```
(Ignore the warnings you get. Just press "enter")

```
sudo lilo -M /dev/sdc mbr
```

Since you are only answering  half of my question and never provide more than a minimum amount  of information, I no longer willing to work on this case.
Good  luck with your problem.

---

### Post by jcobban on 2010-02-18
I am having the same problem on a Compaq Presario CQ60 dual booting between Karmic and Windows 7.  If I reinstall Windows 7 from the upgrade CD, the system will dual boot for a few days but eventually the Win 7 boot fails with the symptoms described in this thread:  The Win 7 boot starts, the Windows logo forms on the screen, then the screen blinks, goes black, the BIOS restarts, and then GRUB boots again.

grub.cfg:
```

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set f81f4681-6cb9-46e7-9262-d5f57c723774
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f81f4681-6cb9-46e7-9262-d5f57c723774
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=f81f4681-6cb9-46e7-9262-d5f57c723774 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f81f4681-6cb9-46e7-9262-d5f57c723774
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=f81f4681-6cb9-46e7-9262-d5f57c723774 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f81f4681-6cb9-46e7-9262-d5f57c723774
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f81f4681-6cb9-46e7-9262-d5f57c723774 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f81f4681-6cb9-46e7-9262-d5f57c723774
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f81f4681-6cb9-46e7-9262-d5f57c723774 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f81f4681-6cb9-46e7-9262-d5f57c723774
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f81f4681-6cb9-46e7-9262-d5f57c723774 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set f81f4681-6cb9-46e7-9262-d5f57c723774
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f81f4681-6cb9-46e7-9262-d5f57c723774 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 34e0e317e0e2de5c
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 64e2185ee2183730
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```
ls /etc/grub.d:
```

$ ls -l /etc/grub.d
total 32
-rwxr-xr-x 1 root root 3296 2009-10-23 20:44 00_header
-rwxr-xr-x 1 root root 1154 2009-10-23 20:31 05_debian_theme
-rwxr-xr-x 1 root root 3778 2009-10-23 20:44 10_linux
-rwxr-xr-x 1 root root  772 2009-10-23 12:11 20_memtest86+
-rwxr-xr-x 1 root root 5467 2009-12-07 18:08 30_os-prober
-rwxr-xr-x 1 root root  214 2009-10-23 20:44 40_custom
-rw-r--r-- 1 root root  483 2009-10-23 20:44 README


```

---

### Post by TransitMan on 2010-02-19
> **meierfra. said:**
> More information please. Did the new entry show up on the Grub? Did you get the same "black screen and reboot"?

According to RESULTS.txt,  you don't have any Windows Entry on the Grub Menu. Also the scripts 30_os-prober and 40_custom did not run. Did you disable them?

Could you post the output  of

```
ls -l /etc/grub.d
```

While we were in a lull in trying to get this working, I was moving the SATA connection around and also edited scripts 30_os-prober and 40_custom , but failed to make them executable again.

Also, I have given you all the information I have, including what I had done prior to posting here for assistance, as explained in my original posting. I was looking for other options not tried in those posts I had found and read, some of them where you had posted and successfully helped others.
I am sorry you feel it is not worth your time to help any further for a lack of information on my part, but in real life, one deals with issues in the house as well as the computer.

I have wiped out Win7 and reinstalled WinXP. I'll see how that one fairs as opposed to Win7.

Peace and long life.

---

### Post by meierfra. on 2010-02-19
jcobban:  Could you start a new thread  with your problem. Also  follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULT.txt in your new thread.

---

### Post by meierfra. on 2010-02-19
TransitMan: Sorry for my  post #12. I spend to much time helping in the forums yesterday and was worn out.

But still, you should always try to provide as much information as possible. A response like "it didn't work" is pretty useless.  Also while following somebodies instruction, don't  try your own fixes at the same time. At least you should asked first.  Otherwise things just get to confusing.

If  you are still having problems, I will be glad to assist you again. There are at least two  more things one can try: Using Legacy Grub and adding Ubuntu to the Windows  boot loader. I know  you already tried whose, but since  you have some many hard drives, it is difficult to set up  things correctly. For example the entry you had for Window 7 on menu.lst  was definitely messed up.

---

### Post by TransitMan on 2010-02-20
> **meierfra. said:**
> TransitMan: Sorry for my  post #12. I spend to much time helping in the forums yesterday and was worn out.

But still, you should always try to provide as much information as possible. A response like "it didn't work" is pretty useless.  Also while following somebodies instruction, don't  try your own fixes at the same time. At least you should asked first.  Otherwise things just get to confusing.

If  you are still having problems, I will be glad be assist you again. There are at least two  more things one can try: Using Legacy Grub and adding Ubuntu to the Windows  boot loader. I know  you already tried whose, but since  you have some many hard drives, it is difficult to set up  things correctly. For example the entry you had for Window 7 on menu.lst  was definitely messed up.

As soon as I possibly can, I will. 
At the moment home issues have come to the forefront and I need to address those first, so I will have to come back to this at another time, hopefully yet this weekend, but.
Sorry about the mis-communications.

---

### Post by TransitMan on 2010-02-22
> **meierfra. said:**
> If  you are still having problems, I will be glad be assist you again. There are at least two  more things one can try: Using Legacy Grub and adding Ubuntu to the Windows  boot loader. I know  you already tried whose, but since  you have some many hard drives, it is difficult to set up  things correctly. For example the entry you had for Window 7 on menu.lst  was definitely messed up.

OK. I had some free time and did some more investigating. It seems there is some type of problem with dual booting more than one hard drive with a boot loader in the BIOS of my motherboard. It is an Intel 915PGN, and it has the last BIOS update available from Intel.
The BIOS boot menu lists only one IDE drive and one SATA, with an option to disable the choice entirely. 
Based on this revelation, I am now thinking of carving my 640 GB drive up with Windows 7 first and Ubuntu behind it. If I am booting off one drive, maybe I can dual-boot working.

Thanks for your help and efforts. I'll let you know if I am successful or not.

---

### Post by meierfra. on 2010-02-22
> Ok, completed the above and came up with booting from the sdc drive into Ubuntu but not Windows7.

> It seems there is some type of problem with dual booting more than one hard drive with a boot loader in the BIOS of my motherboard. I

You were able to boot from sdc and then load Ubuntu on /dev/sda.  This seems to indicated that both sda and sdc were enabled in the bios.    So I'm not sure that putting Window 7 and Ubuntu on the same drive will solve your problem.  But its definitely worth a try.

---

### Post by TransitMan on 2010-02-22
Well, it did not work. Win7 is just a piece of junk when it comes to dual booting.
I guess, when I really want or need to, I'll resort to the BIOS setting for first drive boot.
Everything else I do is in Ubuntu and either WINE or VirtualBox PUEL.

Thanks for trying.

---

