---
title: "The disk drive /home is not ready or not present..."
date: 2011-04-26
forum: General Help
---

### Post by killabee44 on 2011-04-26
Guys,

Im having the above problem with my Ubuntu install not detecting my /home partition. 

I researched other threads with this problem but haven't found an official fix. 

I have 5 hardrives on this machine and am currently trying to consolidate them and get rid of old installs but haven't done anything yet. 

The drive that contains the problem is SDE and the partition that contains the /home on that drive is either sde5 or sde6. I'm almost sure it's sde6. Im also dual booting with windows XP on that drive.

In the meantime, Im booting from an old Kubuntu install that I have on drive SDB.

Please let me know how to proceed. Your help is much appreciated.

Here are the results of the Boot Info Script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x043f043e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   781,419,743   781,419,681   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70667066

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   681,846,794   681,846,732   7 HPFS/NTFS
/dev/sdb2         681,846,856   976,768,064   294,921,209   f W95 Ext d (LBA)
/dev/sdb5         681,846,858   765,818,549    83,971,692   7 HPFS/NTFS
/dev/sdb6         765,818,613   804,888,629    39,070,017  83 Linux
/dev/sdb7         804,888,693   945,521,639   140,632,947  83 Linux
/dev/sdb8         945,521,703   953,329,229     7,807,527  82 Linux swap / Solaris
/dev/sdb9         953,329,293   976,768,064    23,438,772   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4c5d0935

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x127589c5

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05ec2e83

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63    10,442,249    10,442,187  83 Linux
/dev/sde3          10,442,311   133,323,434   122,881,124   5 Extended
/dev/sde5          10,442,313    47,311,424    36,869,112  83 Linux
/dev/sde6          47,311,488   129,226,859    81,915,372  83 Linux
/dev/sde7         129,226,923   133,323,434     4,096,512  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        6A2003182002EAC1                       ntfs       DShares                       
/dev/sdb1        5C108B76108B5644                       ntfs                                     
/dev/sdb5        041CF2611CF24CE4                       ntfs                                     
/dev/sdb6        9ad9b379-56ca-46b7-8b5e-802747ad6f37   ext3                                     
/dev/sdb7        5ccf003e-a3ff-449a-b53e-463c8d372f99   ext3                                     
/dev/sdb8        a9a028d4-46b3-4302-8886-9fd4073a25ff   swap                                     
/dev/sdb9        BC4A-7D67                              vfat                                     
/dev/sdc1        B420A64C20A61600                       ntfs       250 Backup                    
/dev/sdd1        70B4D348B4D31008                       ntfs       250 Newsleecher               
/dev/sde1        7da942e3-c53e-4ae0-9eb2-fce99c412c28   ext3                                     
/dev/sde5        d9ee156c-73e9-4835-81a0-58e7fd06db46   ext4                                     
/dev/sde6        70654c20-ab48-4b64-8fe6-ffda45dd7146   ext4                                     
/dev/sde7        0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb9        /dos                     vfat       (rw,utf8,umask=007,gid=46)
/dev/sdb7        /home                    ext3       (rw,relatime)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=6

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9ad9b379-56ca-46b7-8b5e-802747ad6f37

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
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic


title		Ubuntu 9.04, memtest86+
uuid		9ad9b379-56ca-46b7-8b5e-802747ad6f37
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda9
UUID=BC4A-7D67  /dos            vfat    utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=5ccf003e-a3ff-449a-b53e-463c8d372f99 /home ext3    relatime        0       2
# /dev/sda8
UUID=a9a028d4-46b3-4302-8886-9fd4073a25ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#
UUID=5C108B76108B5644 /media/C-Drive ntfs defaults 0 0
#
UUID=041CF2611CF24CE4 /media/D-Drive ntfs defaults 0 0
#
UUID=6A2003182002EAC1 /media/DShares ntfs defaults 0 0
#
UUID=ACC0BC4BC0BC1E10 /media/MiscMovies ntfs defaults 0 0
#
UUID=70B4D348B4D31008 /media/Newsleecher ntfs defaults 0 0
#
UUID=B420A64C20A61600 /media/250Backup ntfs defaults 0 0

music and video 1.5TB
#UUID=2AA91D326971D565 /media/musicandvideo ntfs-3g user,defaults 0 0

#Video 400 
UUID=992ADF057FADABD5 /media/video400 ntfs-3g user,defaults 0 0

=================== sdb6: Location of files loaded by Grub: ===================


 395.3GB: boot/grub/menu.lst
 395.4GB: boot/grub/stage2
 395.3GB: boot/initrd.img-2.6.27-14-generic
 395.4GB: boot/initrd.img-2.6.28-11-generic
 395.3GB: boot/initrd.img-2.6.28-12-generic
 395.3GB: boot/initrd.img-2.6.28-13-generic
 395.3GB: boot/initrd.img-2.6.28-14-generic
 395.4GB: boot/initrd.img-2.6.28-15-generic
 395.4GB: boot/initrd.img-2.6.28-16-generic
 395.4GB: boot/initrd.img-2.6.28-17-generic
 395.5GB: boot/initrd.img-2.6.28-18-generic
 395.3GB: boot/vmlinuz-2.6.27-14-generic
 395.3GB: boot/vmlinuz-2.6.28-11-generic
 395.4GB: boot/vmlinuz-2.6.28-12-generic
 395.3GB: boot/vmlinuz-2.6.28-13-generic
 395.4GB: boot/vmlinuz-2.6.28-14-generic
 395.4GB: boot/vmlinuz-2.6.28-15-generic
 395.4GB: boot/vmlinuz-2.6.28-16-generic
 395.4GB: boot/vmlinuz-2.6.28-17-generic
 395.4GB: boot/vmlinuz-2.6.28-18-generic
 395.5GB: initrd.img
 395.4GB: initrd.img.old
 395.4GB: vmlinuz
 395.4GB: vmlinuz.old

=========================== sde5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set d9ee156c-73e9-4835-81a0-58e7fd06db46
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 5c108b76108b5644
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro single
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro quiet splash
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=9ad9b379-56ca-46b7-8b5e-802747ad6f37 ro single
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 9ad9b379-56ca-46b7-8b5e-802747ad6f37
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 /               ext4    errors=remount-ro 0       1
/dev/sdc6       /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=a9a028d4-46b3-4302-8886-9fd4073a25ff none            swap    sw              0       0
# swap was on /dev/sdc7 during installation
UUID=0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1 none            swap    sw              0       0
#


=================== sde5: Location of files loaded by Grub: ===================


   7.6GB: boot/grub/core.img
  16.6GB: boot/grub/grub.cfg
   7.9GB: boot/initrd.img-2.6.32-21-generic
   8.4GB: boot/initrd.img-2.6.32-22-generic
   8.5GB: boot/initrd.img-2.6.32-23-generic
   8.9GB: boot/initrd.img-2.6.32-24-generic
  11.4GB: boot/initrd.img-2.6.32-25-generic
  17.1GB: boot/initrd.img-2.6.32-26-generic
  13.4GB: boot/initrd.img-2.6.32-27-generic
   9.3GB: boot/initrd.img-2.6.32-28-generic
   7.7GB: boot/vmlinuz-2.6.32-21-generic
  18.6GB: boot/vmlinuz-2.6.32-22-generic
   9.4GB: boot/vmlinuz-2.6.32-23-generic
   8.4GB: boot/vmlinuz-2.6.32-24-generic
   8.7GB: boot/vmlinuz-2.6.32-25-generic
   8.9GB: boot/vmlinuz-2.6.32-26-generic
   8.9GB: boot/vmlinuz-2.6.32-27-generic
   8.7GB: boot/vmlinuz-2.6.32-28-generic
   9.3GB: initrd.img
  13.4GB: initrd.img.old
   8.7GB: vmlinuz
   8.9GB: vmlinuz.old
```

---

### Post by idoitprone on 2011-04-26
```
=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 /               ext4    errors=remount-ro 0       1
**/dev/sdc6       /home           ext4    defaults        0       **2
# swap was on /dev/sda8 during installation
UUID=a9a028d4-46b3-4302-8886-9fd4073a25ff none            swap    sw              0       0
# swap was on /dev/sdc7 during installation
UUID=0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1 none            swap    sw              0       0
#
```

> The drive that contains the problem is SDE and the partition that contains the /home on that drive is either sde5 or sde6. I'm almost sure it's **sde6**. Im also dual booting with windows XP on that drive.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

For one thing, your drive are all over the place. I believe the problem is that your ubuntu install is not pointing to the right hard drive. Your said you home partition is on sd**e**6, but your /etc/fstab/ points to sd**c**6. I believe that is your problem. Why does it say root is on sdc5, even though the uuid is sde6? This looks very confusing. Also, it why is it using swap on two different harddrive? I guess it might be faster. Go to that link and take a look

---

### Post by killabee44 on 2011-04-26
Yeah, It looks like somehow that got changed. Weird though, because I don't know how that happened. Ill change it to SDE6 and post back.

---

### Post by Quackers on 2011-04-26
Which drive is set to boot first?
What does the grub menu say at the top? Which grub version is shown?

---

### Post by killabee44 on 2011-04-26
Guys,

Thanks for your replies...

I got it worked out. The problem was that fstab file which was all screwed up. Not sure how that happened since all was working ok before. Anyhow, I got it to boot by specifying: 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation

#ROOT:
UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 /               ext4   
 
#HOME:
UUID=70654c20-ab48-4b64-8fe6-ffda45dd7146 /home           ext4 
   
# swap
UUID=0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1 none            swap    sw              0       0
#

```

As you can see I took out the other swap. Working great now. 

One thing I wanted to ask you guys is how do I move an Ubuntu install to a new hard drive? What is the best way? Would you say I just use a program like Acronis from within Windows?

Is there a better open source solution? Thanks.

---

### Post by idoitprone on 2011-04-26
> **killabee44 said:**
> Guys,

Thanks for your replies...

I got it worked out. The problem was that fstab file which was all screwed up. Not sure how that happened since all was working ok before. Anyhow, I got it to boot by specifying: 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation

#ROOT:
UUID=d9ee156c-73e9-4835-81a0-58e7fd06db46 /               ext4   
 
#HOME:
UUID=70654c20-ab48-4b64-8fe6-ffda45dd7146 /home           ext4 
   
# swap
UUID=0e8dadae-bdba-4c1e-ac8d-d516d38cc2c1 none            swap    sw              0       0
#

```

As you can see I took out the other swap. Working great now. 

One thing I wanted to ask you guys is how do I move an Ubuntu install to a new hard drive? What is the best way? Would you say I just use a program like Acronis from within Windows?

Is there a better open source solution? Thanks.

Reinstall is the best option. If you want an image of your current system clonzeilla

---

### Post by killabee44 on 2011-04-26
Ok, so if I reinstall and bring over my home directory Im guessing that would work ok? But I would have to reinstall all my programs correct?

---

### Post by idoitprone on 2011-04-26
> **killabee44 said:**
> Ok, so if I reinstall and bring over my home directory Im guessing that would work ok? But I would have to reinstall all my programs correct?

moving over an harddrive is the same as backing it up. yep that should work.

---

### Post by oldfred on 2011-04-26
You can list and reinstall all your apps. I do this as I like to do clean installs. But you also should houseclean and perhaps edit out some old versions if upgrading. ( I find I still am reinstalling python 2.5 for no reason). But I will houseclean it out for next time.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

The above and this should be part of your normal backups any way.
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup

sudo cp /etc/apt/sources.list ~/sources.list.backup
sudo apt-key exportall > ~/repositories.key

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

I also run a bootscript and a couple of the hardware listing just to have the documentation of the system in my backups.

---

### Post by killabee44 on 2011-04-27
Real valuable info... thanks. 


Im gonna mirror the Windows dual boot partition on this drive over to the new drive. 

Then reinstall LTS on that drive and copy all the home folder files, reinstall all the apps per the above procedure and also do the rest on that list (1-4). 

**(Should I copy the home folder over to the new drive before the install?) <--I wasn't sure about this..

After the install and restore is done:

I have a 250 gig Backup drive that I can back up images to. 

So, after I have the new drive situated, What do you guys recommend for an image backup of my ubuntu install on the backup drive? 

Ive been reading Rsync is good. What do you think?

---

### Post by oldfred on 2011-04-27
As long as you have old drive, it is a lot easier as you can still go back. I do clean installs, but always to a new partition. I rotate several / (root) partitions around so I have 3 or more working Ubuntus. Old version, current version, testing of alpha/beta.  I can then always boot something and if I forget something else I can go back.

Do not just copy /etc or the sources list if a new version. Save or any extra settings you may have added, but new versions may be different and old ones may cause problems. I do not copy all /etc and have only found a couple of cases where I could use the old setting to make it easier to reconfigure.

I would copy /home over first so you can immediately mount it as part of the install. Just do not format it.

I have only backed up data and some settings but never full system. I do not have anything critical and assume I will just do a new install if I ever have a major crash. I like rsync for the data I do backup.

---

