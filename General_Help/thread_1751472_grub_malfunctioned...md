---
title: "grub malfunctioned.."
date: 2011-05-06
forum: General Help
---

### Post by tetsu7 on 2011-05-06
so im just surfing the internet for a new laser printer when my computer freezes so i do a hard restart. instead of the grub boot loader i get a grub rescue prompt. im back in my system now via super grub disk 1.98 my question is how can i get grub back up and working? im running ubuntu 10.10 on a crucial SSD dual booted with win7 on a hitachi HDD. thank you in advance for any advice!

---

### Post by oldfred on 2011-05-06
You can easily reinstall grub2 to the MBR of your drive from a working system. But after a crash I find grub not working unusual. Normally you would have to run e2fsck file checks to correct a partition issue from a liveCD. Are all your partitions mounting ok?

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by tetsu7 on 2011-05-06
i ran sudo fdisk -l and returned the following results:

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ccb55

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14929   119910400   83  Linux
/dev/sdb2           14929       15567     5122049    5  Extended
/dev/sdb5           14929       15567     5122048   82  Linux swap / Solaris

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x001d709d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         975     7831520+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(973, 254, 63) logical=(974, 250, 44)


#if it's "/dev/sdb" then just run:
sudo grub-install /dev/sdb

i assumed since it said "linux" on /dev/sdb1 to run sudo grub-install /dev/sdb1

then i ran: 

sudo grub-install /dev/sdb
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

still get rescue prompt so i did this:

sudo grub-install --recheck /dev/sdb

Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

still rescue prompt so then:

sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-2.6.35-28-generic
Found kernel: /boot/vmlinuz-2.6.35-25-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

and then:

sudo dpkg-reconfigure grub-pc
/usr/sbin/dpkg-reconfigure: grub-pc is broken or not fully installed

and when using super grub disk 1.98 to boot the OS i choose to detect overwritten grub2 and when it finds it it says this:
load /boot/grub/core.img from (hd1,1)
so still no grub any other ideas?

---

### Post by drs305 on 2011-05-06
You appear to have a mixture of Grub legacy and Grub2. To update Grub2, it looks like 'update-grub' is invoking Grub legacy. Try this if you are in your working Ubuntu installation:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

It might help to see all your boot information. Please download the boot info script and post the contents of RESULTS.txt:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by tetsu7 on 2011-05-06
and ive got an IDE dvd drive that ive unplugged because i couldnt boot from the super grub disk nor the ubuntu disk and previously (when my grub more or less worked) when i went into recovery mode it would freeze after it read the dvd drive which is only a little over a year old lightscribe. so i unplugged it and i am using a mad dog external dvd drive via usb. i am now thinking my dvd drive may have been incompatable with the OS? before all this happened ive been having trouble booting my OS, i would get the grub everytime but when i seleced ubuntu more often then not it would just hang with a cursor in the upper left hand corner. i had the latest nvidia driver installed. had the same problem with the nvidia 173 driver as well. could that have been due to the dvd drive?

---

### Post by tetsu7 on 2011-05-06
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for cch.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 512002048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 168279888 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on the same partition for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
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

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   512,002,047   511,795,200   7 HPFS/NTFS
/dev/sda3         512,002,048 1,953,523,711 1,441,521,664   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   239,822,847   239,820,800  83 Linux
/dev/sdb2         239,824,894   250,068,991    10,244,098   5 Extended
/dev/sdb5         239,824,896   250,068,991    10,244,096  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    15,663,103    15,663,041   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        06626121626116A9                       ntfs       System Reserved               
/dev/sda2        4A046CEE046CDE87                       ntfs                                     
/dev/sda3        34EC-C51B                              vfat       fat32 share                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a8b0292c-05e8-45c7-a501-94002905db65   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        c4137a49-0ffa-45e1-8672-4ff529f64342   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8CE0-01F4                              vfat                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/8CE0-01F4         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a8b0292c-05e8-45c7-a501-94002905db65

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

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		a8b0292c-05e8-45c7-a501-94002905db65
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		a8b0292c-05e8-45c7-a501-94002905db65
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		a8b0292c-05e8-45c7-a501-94002905db65
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		a8b0292c-05e8-45c7-a501-94002905db65
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Chainload into GRUB 2
root		a8b0292c-05e8-45c7-a501-94002905db65
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		a8b0292c-05e8-45c7-a501-94002905db65
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=a8b0292c-05e8-45c7-a501-94002905db65 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a8b0292c-05e8-45c7-a501-94002905db65
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 06626121626116a9
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=a8b0292c-05e8-45c7-a501-94002905db65 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=c4137a49-0ffa-45e1-8672-4ff529f64342 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  86.1GB: boot/grub/core.img
 116.6GB: boot/grub/grub.cfg
  86.1GB: boot/grub/menu.lst
  86.1GB: boot/grub/stage2
   2.8GB: boot/initrd.img-2.6.35-25-generic
   6.3GB: boot/initrd.img-2.6.35-28-generic
  86.0GB: boot/vmlinuz-2.6.35-25-generic
   6.1GB: boot/vmlinuz-2.6.35-28-generic
   6.3GB: initrd.img
   2.8GB: initrd.img.old
   6.1GB: vmlinuz
  86.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  19 b4 39 60 d6 59 bf 79  9a 70 11 21 5d 0e 1b 00  |..9`.Y.y.p.!]...|
00000010  55 ec d6 9b 11 6e f0 f3  eb 19 e2 24 46 db be ce  |U....n.....$F...|
00000020  ed 4e 12 aa 36 ee a2 fc  8e 24 8c 47 3b bc a1 1f  |.N..6....$.G;...|
00000030  4f 86 3a 93 c5 fe dc a1  b9 1c 47 5e 98 8a 27 ec  |O.:.......G^..'.|
00000040  18 67 1a 1c 5b dd 8c 37  96 20 4d 87 ac 0a da 9e  |.g..[..7. M.....|
00000050  f4 2a ec 4a 7d 82 cc 92  92 02 31 14 60 70 0d 78  |.*.J}.....1.`p.x|
00000060  df 24 5b a8 ac 16 86 51  6a 7e e4 cb 62 ad b0 1b  |.$[....Qj~..b...|
00000070  4b a6 90 16 b8 46 e5 cb  2d eb de 97 35 ea 35 e0  |K....F..-...5.5.|
00000080  e8 82 48 26 6b 70 07 46  48 4b 69 26 bc 62 1f 31  |..H&kp.FHKi&.b.1|
00000090  d6 8a da f7 77 30 b5 53  9b d9 b6 66 88 d0 df 0c  |....w0.S...f....|
000000a0  a6 4f 33 d0 03 cc 33 1f  9f b7 02 c8 62 fd 52 7e  |.O3...3.....b.R~|
000000b0  05 f7 bc 51 2f c1 7d 7b  15 e2 de 6d e0 5a 9e 43  |...Q/.}{...m.Z.C|
000000c0  5a 11 a9 78 5e 32 2a a7  cc e5 cb 8d 90 5b f3 6e  |Z..x^2*......[.n|
000000d0  53 93 58 56 06 e9 92 44  2b 98 47 4f 07 26 38 4b  |S.XV...D+.GO.&8K|
000000e0  53 33 28 62 3f 6d 52 1d  f4 24 47 b7 75 f9 ce 24  |S3(b?mR..$G.u..$|
000000f0  76 85 46 f6 55 29 c4 99  f5 b3 83 48 ec ed 6f d6  |v.F.U).....H..o.|
00000100  74 a8 d3 19 cc 83 99 0a  05 9b 9f fd 5f 32 8f eb  |t..........._2..|
00000110  a9 b4 06 3e c9 a5 34 9b  a1 aa 51 62 21 35 b4 af  |...>..4...Qb!5..|
00000120  74 af ad b9 a8 76 c6 d3  94 36 4d 2d 2e 26 86 9a  |t....v...6M-.&..|
00000130  38 4c 13 9e 95 87 c2 09  b2 e0 cf 6d d7 8e de c3  |8L.........m....|
00000140  bd 72 7f 59 5a 95 37 49  1b f8 54 37 f5 f2 fb 2e  |.r.YZ.7I..T7....|
00000150  91 f6 88 c8 c1 89 f4 8c  eb b7 17 e1 0f b8 74 f1  |..............t.|
00000160  4c c8 17 b9 24 7d 0a d0  37 40 ff 49 ec 23 78 13  |L...$}..7@.I.#x.|
00000170  38 cd 41 cc 2b a1 73 34  10 da e1 27 56 65 0e 8e  |8.A.+.s4...'Ve..|
00000180  c4 14 ea 02 30 d7 19 ab  5d f7 c7 0a c7 71 ec df  |....0...]....q..|
00000190  c4 00 f7 ee e3 fc 6f e4  dd 24 e3 e4 0d 8c e2 1b  |......o..$......|
000001a0  9b a0 28 3e 07 ad 01 84  01 2e c8 10 2c c5 f9 88  |..(>........,...|
000001b0  f4 60 71 67 35 a7 aa a7  38 40 8b c7 bc ae 00 fe  |.`qg5...8@......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 9c 00 00 00  |...........P....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg

```

---

### Post by tetsu7 on 2011-05-06
i read somewhere to install grub from the terminal may help so i did. shortly thereafter i realized that grub2 was grub-pc and had since tried to reinstall it and failed.

---

### Post by tetsu7 on 2011-05-06
sudo grub-mkconfig -o /boot/grub/grub.cfg
 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

---

### Post by drs305 on 2011-05-06
If you are currently booted into your normal Ubuntu installation on sdb1, I'd recommend purging grub, grub-pc, and grub-common, and then reinstalling grub-common and grub-pc. As long as you have a working Internet connection this process is very simple. Just confirm your Ubuntu drive is still **sdb** before running the commands:

```
sudo apt-get update # If this doesn't run correctly, stop here.
sudo apt-get purge grub grub-pc grub-common # You will be warned about losing your bootloader.
sudo apt-get install grub-pc # Will install grub-pc and grub-common

```
When asked for kernel options, you don't currently have any so TAB to OK and ENTER.

When asked where to install, TAB to **sdb** and press the SPACEBAR to put an asterisk on **sdb**. TAB to OK, ENTER. Do NOT  put an asterisk next to any partition.

Reboot.

---

### Post by wilee-nilee on 2011-05-06
Oops see drs305 for this.;)

---

### Post by tetsu7 on 2011-05-06
followed your instructions exactly no errors reported. after reboot i got the same thing:
error: no such device: 396905fe-0d8c-4ded-aad3-9e49fe3c05f9

grub rescue prompt again.

---

### Post by drs305 on 2011-05-06
> **tetsu7 said:**
> followed your instructions exactly no errors reported. after reboot i got the same thing:
error: no such device: 396905fe-0d8c-4ded-aad3-9e49fe3c05f9

grub rescue prompt again.

I don't see that listed in RESULTS.txt as a UUID for any partition.

At the grub prompt, press 'e' to edit the first menuentry.
Use the cursors and DEL key to remove the 'search' line.
On the linux line, change the part that reads:
> ... root=UUID=<some long alphanumeric> ...
to
... root=/dev/sdb1 ....
Then CTRL-x and see if it boots. If this doesn't work, we'll try a manual boot via command line.

---

### Post by tetsu7 on 2011-05-06
problem solved thank you very much! your commands worked i had just had to switch the boot order in my BIOS as i had been booting from the HDD but am now booting from the SSD. (i had tried both while troubleshooting) again thank you for your prompt replies and your great advice in this matter you were very professional and very knowledgeable! i copied those commands to a text file for later use if needed.

---

