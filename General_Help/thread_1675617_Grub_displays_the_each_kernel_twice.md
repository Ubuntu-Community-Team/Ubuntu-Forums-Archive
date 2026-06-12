---
title: "Grub displays the each kernel twice"
date: 2011-01-25
forum: General Help
---

### Post by snlzkn on 2011-01-25
I have removed all the kernels other than 35-25 and 32-28. I want to keep them but even though I can see only those two when I look in Synaptic, when I run update-grub I get two entries for each kernel. I have added the result of update-grub. This makes my grub list really long. Any ideas? Can one of them be custom compilation generated while installing something. May be then it would have exactly the same number but not show on synaptic package manager? How can I check if that is so or not?

Edit: I am using Ubuntu 10.10 and have ATI Catalyst as graphics driver.

```
snlzkn@semender:~$ sudo update-grub
[sudo] password for snlzkn: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1

```

---

### Post by coffeecat on 2011-01-26
Normally, you would have two entries in the grub menu for each version of the kernel, a normal entry and a recovery mode entry. So, for two versions of the kernel that would be four menu entries altogether (ignoring the memtest entries). But your update-grub output does look as though it is counting each kernel twice. Do you have four or eight kernel entries altogether?

If you have eight, go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script and post the results.txt file within code tags for legibility. You can do this with the # icon in the message toolbar. That will tell us what is on your system and, hopefully, why each kernel is being counted twice.

---

### Post by snlzkn on 2011-02-04
Sorry for the late reply. The kernel and its recovery both of them are repeated so I ran the script and here is the result file.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 228653145.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   186,289,739   186,289,677   7 HPFS/NTFS
/dev/sda2         186,289,740   228,653,144    42,363,405  83 Linux
/dev/sda3         228,653,145   625,137,344   396,484,200   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C814E0FA14E0EC7E                       ntfs                                     
/dev/sda2        36d89f30-f49a-4d1b-ab7a-6fcaf0507eec   ext4                                     
/dev/sda3        848492F38492E748                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,commit=0)
/dev/sda1        /media/Win7OS            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=512)


=========================== sda2/boot/grub/menu.lst: ===========================

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
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec

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
title		Windows 7
rootnoverify	(hd0,0)
savedefault
chainloader +1

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Chainload into GRUB 2
root		36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1400x1050
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro  splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro  splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro  splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro  splash  quiet splash nomodeset video=uvesafb:mode_option=1400x1050-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 36d89f30-f49a-4d1b-ab7a-6fcaf0507eec
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c814e0fa14e0ec7e
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=36d89f30-f49a-4d1b-ab7a-6fcaf0507eec /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1	/media/Win7OS	ntfs,user,auto,umask=0 0 0
/dev/sda3	/media/DATA	ntfs,user,auto,umask=007,uid=1000,gid=1000 0 1
/swapfile	swap		swap	defaults
tmpfs		/dev/shm 	tmpfs	defaults	0	0

=================== sda2: Location of files loaded by Grub: ===================


  95.5GB: boot/grub/core.img
 100.6GB: boot/grub/grub.cfg
  96.5GB: boot/grub/menu.lst
 102.9GB: boot/initrd.img-2.6.32-28-generic
 111.8GB: boot/initrd.img-2.6.35-25-generic
 111.9GB: boot/vmlinuz-2.6.32-28-generic
 113.2GB: boot/vmlinuz-2.6.35-25-generic
 111.8GB: initrd.img
 102.9GB: initrd.img.old
 113.2GB: vmlinuz
 111.9GB: vmlinuz.old
```

---

### Post by coffeecat on 2011-02-04
The reason why both kernels are appearing twice is that update-grub is parsing a file called /etc/grub.d/10_linux_proxy which must contain references to both kernels. Which, as far as I can see, is superfluous because update-grub detects any kernels on the system by  parsing /etc/grub.d/10_linux.

The fix is simple, but before I give that a couple of comments. I've never seen a 10_linux_proxy file before - it is on none of my systems - but a quick google throws up plenty of threads on this forum where people's boot script output show the presence of this file. It must have come from somewhere. :? I'll dig a little deeper, but in the meantime, please post the contents of your /etc/grub.d/10_linux_proxy file. The comments at the beginning of the file might give us a clue. I see that you have a remnant of legacy grub, so you must have updated from legacy grub to grub2 - perhaps it's something to do with that. Please also post the output of:

```
ls /etc/grub.d/
```It will be useful to know if any other non-standard files are in there as well.

The fix. This will stop update-grub parsing the 10_linux_proxy file, at least for now, but we do need to find out how it got there. It may have been important. From a terminal:

```
sudo chmod -x /etc/grub.d/10_linux_proxy
```Now regenerate grub.cfg with:

```
sudo update-grub
```

---

### Post by Quackers on 2011-02-04
You also appear to be running 10.10, and consequently have grub2 installed in the mbr of the drive. However, in sda2 you have one of grub legacy's files (/boot/grub/Menu.lst). Have you repaired grub2 at any time? Perhaps with an old guide?

---

### Post by coffeecat on 2011-02-04
I've been doing a bit of digging on this forum only for the time being and those threads that show 10_linux_proxy in grub.cfg in a boot script output do not show any reference to 10_linux - which is the usual file. But your grub.cfg shows both. Before you run the chmod command I posted, make sure you do have a /etc/grub.d/10_linux file with something in it. Since grub.cfg says you have, I'm 99.9999% sure that it's OK to disable  the 10_linux_proxy file by chmodding it, but I'd like to resolve the 0.0001% uncertainty. :)

---

### Post by grahammechanical on 2011-02-04
May I direct you or anyone else to this link?

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

I downloaded Grub Customizer yesterday. It is a brilliant utility that allows you to remove menu entries using a GUI. It does lots of other things too.

Regards.

---

### Post by snlzkn on 2011-02-04
Hello the contents of /etc/grub.d

```

00_header                 10_linux_proxy  40_custom         README
05_debian_theme           20_linux_xen    41_custom
05_debian_theme.dpkg-old  20_memtest86+   bin
10_linux                  30_os-prober    proxifiedScripts

```

I checked that I have 10_linux file with some content :) This is my 10_linux_proxy file. It has only old kernels which do not show anyways :S

```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/linux' | /etc/grub.d/bin/grubcfg_proxy "+*
+'Ubuntu, with Linux 2.6.32-24-generic'
+'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)'
-'Ubuntu, with Linux 2.6.32-23-generic'
-'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)'
-'Ubuntu, with Linux 2.6.32-22-generic'
-'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)'
+'Ubuntu, with Linux 2.6.32-21-generic'
+'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)'
"
```

By the way I switched to grub2 on my own when I was using 9 something I am not sure. May be 10.04. I was using grub2 when I upgraded to 10.10. I recently recovered my grub2 after Windows 7 installation without using the live cd. I used NeoGrub under windows to load my grub2. Which worked and in ubuntu I used update-grub to put things back in order. I tried to install gnome3 and it always did not work. I tried to build it again gave errors always at different steps and I gave up eventually but my system really got unstable I think. Where should I look for the remains of grub_legacy. Is new grub2 also using boot/grub folder?

I did the chmod and it looks like it solved the problem. I checked it using the grub customizer. I had 2 different linux entries with the same content and one of them became unchecked after doing chmod -x. I think I will remove that script from the configuration using the grub-customizer after restarting once :D

Thanks for the help. Now next challenge is getting gnome3 to work :)

---

### Post by coffeecat on 2011-02-04
Fascinating. I think I can see what 10_linux_proxy is up to now that I can see what's in it. What is interesting is that not only do I not have 10_linux_proxy in /etc/grub.d/, but no bin or proxifiedScripts files/folders either. I guess they are all of a package with whatever added 10_linux_proxy. I'm still curious to know what that was though.

For the record, this is the contents of my /etc/grub.d/, Maverick freshly installed only yesterday, so near as default as you're going to get:

```
$ ls /etc/grub.d/
00_header        10_linux      20_memtest86+  40_custom  README
05_debian_theme  20_linux_xen  30_os-prober   41_custom
```Good luck with gnome 3. Unity in Natty Alpha is enough to keep me out of mischief for the time being. :)

---

