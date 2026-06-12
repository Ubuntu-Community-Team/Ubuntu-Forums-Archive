---
title: "Grub can't find window 7 installed after ubuntu"
date: 2012-01-31
forum: General Help
---

### Post by jirtar on 2012-01-31
I first install ubuntu 10.10 many month ago on the entire hard drive. today i decide to install window 7. I gparted the hard drive. and install window 7.

when i finish installing window 7 i use the ubuntu install cd and do the following:

sudo mount /dev/sda1 /mnt

sudo -i
grub-install --root-directory=/mnt/ /dev/sda

but when i boot, i don't have the grub menu and after alot of 
trouble i finally get the menu but window 7 not there

Gparted show the hard drive partionned this way:

sda1 ext4 linux, sda2 ntfs win7 (flags: boot), sda3 extended, sda5 linux-swap

try many way on the net but none of them work. grub menu don't list window 7
and can't boot it. It is possible (and how) to add it to grub and boot it or need to wipe the entire disk and start from zero?

---

### Post by westie457 on 2012-01-31
Hi.
Welcome to the Forum.

You did well to do what you did, all you forgot was to run the update-grub command.

So all you need to do now is boot into your Ubuntu, open a terminal and run ```
sudo update-grub
```

Watch the output on the screen, If Windows is not found we will have to try something else.

---

### Post by jirtar on 2012-01-31
sorry forget to mention it, it try this too. :(

---

### Post by raja.genupula on 2012-01-31
Hi 

 

please give us the output of bootinfoscript (at my signature ) .

---

### Post by goofey24 on 2012-01-31
It's wise to install Windows 7 FIRST then Ubuntu.:p

---

### Post by jirtar on 2012-01-31
here the result of boot_info_script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   319,447,039   319,444,992  83 Linux
/dev/sda2    *    319,447,040   958,343,167   638,896,128   7 NTFS / exFAT / HPFS
/dev/sda3         958,345,214   976,771,071    18,425,858   5 Extended
/dev/sda5         958,345,216   976,771,071    18,425,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        41859590-22d8-46f7-b18e-45f8fe77cc3c   ext4       
/dev/sda2        30A02656117B6509                       ntfs       
/dev/sda5        6eda1b52-099a-403b-a2bb-4d93d3265971   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
timeout		8

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
# kopt=root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=41859590-22d8-46f7-b18e-45f8fe77cc3c

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

title		Ubuntu 10.10, kernel 2.6.35-32-generic
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-32-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro quiet splash 
initrd		/boot/initrd.img-2.6.35-32-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-32-generic (recovery mode)
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-32-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro  single
initrd		/boot/initrd.img-2.6.35-32-generic

title		Ubuntu 10.10, kernel 2.6.35-30-generic
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-30-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro quiet splash 
initrd		/boot/initrd.img-2.6.35-30-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-30-generic (recovery mode)
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-30-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro  single
initrd		/boot/initrd.img-2.6.35-30-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic
quiet

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		41859590-22d8-46f7-b18e-45f8fe77cc3c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	linux	/boot/vmlinuz-2.6.35-32-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	echo	'Loading Linux 2.6.35-32-generic ...'
	linux	/boot/vmlinuz-2.6.35-32-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 41859590-22d8-46f7-b18e-45f8fe77cc3c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda1 :
UUID=41859590-22d8-46f7-b18e-45f8fe77cc3c	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda2 :
UUID=30A02656117B6509	/media/sda2	ntfs-3g	defaults,locale=en_CA.utf8	0	0
#Entry for /dev/sda5 :
UUID=6eda1b52-099a-403b-a2bb-4d93d3265971	none	swap	sw	0	0


--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   3.907054901 = 4.195168256    boot/grub/core.img                             1
   6.129951477 = 6.581985280    boot/grub/grub.cfg                             1
 132.805992126 = 142.599348224  boot/grub/menu.lst                             1
   2.272789001 = 2.440388608    boot/grub/stage2                               1
   0.882102966 = 0.947150848    boot/initrd.img-2.6.35-22-generic              2
   1.132114410 = 1.215598592    boot/initrd.img-2.6.35-28-generic              2
   4.941711426 = 5.306122240    boot/initrd.img-2.6.35-30-generic              2
   4.448551178 = 4.776595456    boot/initrd.img-2.6.35-32-generic              1
   3.981788635 = 4.275412992    boot/vmlinuz-2.6.35-22-generic                 3
   4.041385651 = 4.339404800    boot/vmlinuz-2.6.35-28-generic                 2
   4.063796997 = 4.363468800    boot/vmlinuz-2.6.35-30-generic                 2
   4.049186707 = 4.347781120    boot/vmlinuz-2.6.35-32-generic                 1
   4.448551178 = 4.776595456    initrd.img                                     1
   4.941711426 = 5.306122240    initrd.img.old                                 2
   4.049186707 = 4.347781120    vmlinuz                                        1
   4.063796997 = 4.363468800    vmlinuz.old                                    2

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


```

---

### Post by oldfred on 2012-01-31
Grub legacy 0.97 almost never found Windows 7 and did not always find XP. Grub2's os-prober is so much better that it is worth using grub2 just for that. Is there some reason you install grub legacy?

If you want to convert back to grub2. If you can boot and have internet, you do not have to chroot.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you want to have a Windows entry in menu.lst - be sure to put it before or after the automagic area as grub updates rewrite everything from automagic start to end:

title Windows 7 Ultimate, chainloader (on /dev/sda2)
rootnoverify (hd0,1)
savedefault
chainloader +1

Note that partition numbering in grub legacy is different that in grub2.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by jirtar on 2012-01-31
Fantastic, it works!

The link provided by **oldfred** give a full step by step commented. i follow step 2 to 5.

Here the link again.
[U][COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")
[/COLOR]
[/U]These step have resolved my probleme.
```
2.    sudo apt-get update
3.    sudo apt-get purge grub grub-pc grub-common // i think the magic here is the purge command
4.    sudo apt-get install grub-common grub-pc
	       a. tab enter
	       b. Make sure the installation drive [*] /dev/sdX has an asterisk next to it ( example: [*] /dev/sda ).	
	          If it doesn't, highlight it and press the SPACE bar to select it.
	       c. tab enter
5.    sudo update-grub
```

[size=+2]Thank guy for your help.[/size]

---

### Post by oldfred on 2012-01-31
Glad it worked.

drs305 always has good instructions.:)

---

