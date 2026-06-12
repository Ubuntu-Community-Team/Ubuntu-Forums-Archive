---
title: "Grub Broken"
date: 2011-05-08
forum: General Help
---

### Post by Mike Loubet on 2011-05-08
Hi there,

I upgraded to 11.04 from 10.10. On reboot, the OS wasn't booting and wasn't loading GRUB at all. Reinstalled GRUB using LiveCD, then all I was getting was the grub-rescue command line. Booted using this:

```
set root=(hdX,Y)
linux /vmlinuz root=/dev/sdXY ro
initrd /initrd.img
boot
```

I switched to KDE at this point (by installing plasma-desktop and KDE packages, not fresh install). After doing ```
sudo update-grub
``` and reinstalling GRUB2 a few times, I can still only boot from the command line, even though the command shows that the kernels are present and menu.lst has been updated:

```
mike@Sysem76:~$ sudo update-grub
[sudo] password for mike: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.38-9-generic
Found kernel: /boot/vmlinuz-2.6.38-8-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Why can't I just boot normally?

(Kubuntu 11.04 64 bit)

---

### Post by cipherboy_loc on 2011-05-08
Are you using Grub Legacy? Also, post /boot/grub/grub.cfg and /boot/grub/menu.lst (which ever you have). 


Cipherboy

---

### Post by wilee-nilee on 2011-05-08
> **cipherboy_loc said:**
> Are you using Grub Legacy? Also, post /boot/grub/grub.cfg and /boot/grub/menu.lst (which ever you have). 


Cipherboy

Good eye.;)

So from a booted live Ubuntu cd, thumbdrive, or Ubnutu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Mike Loubet on 2011-05-08
Thanks for the replies :)

Looking at the package list, I have grub (legacy version) and grub-common. Here's the output:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 126092033 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1   145,009,765   145,009,765  83 Linux
/dev/sda2         145,009,766   156,301,487    11,291,722   5 Extended
/dev/sda5         145,009,767   156,301,487    11,291,721  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        552496e2-92cc-4e0f-87c0-322edc0cb632   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5abbcc52-f627-41eb-956f-3f811627ebed   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,noatime,discard,commit=600,commit=600,commit=0,commit=600,commit=0,commit=600)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=552496e2-92cc-4e0f-87c0-322edc0cb632

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

title		Ubuntu 11.04, kernel 2.6.38-9-generic
uuid		552496e2-92cc-4e0f-87c0-322edc0cb632
kernel		/boot/vmlinuz-2.6.38-9-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-9-generic

title		Ubuntu 11.04, kernel 2.6.38-9-generic (recovery mode)
uuid		552496e2-92cc-4e0f-87c0-322edc0cb632
kernel		/boot/vmlinuz-2.6.38-9-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro  single
initrd		/boot/initrd.img-2.6.38-9-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		552496e2-92cc-4e0f-87c0-322edc0cb632
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		552496e2-92cc-4e0f-87c0-322edc0cb632
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Chainload into GRUB 2
root		552496e2-92cc-4e0f-87c0-322edc0cb632
kernel		/boot/grub/core.img

title		Ubuntu 11.04, memtest86+
uuid		552496e2-92cc-4e0f-87c0-322edc0cb632
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 0,71,115; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	nodev,noexec,nosuid	0	0
# / was on /dev/sda1 during installation
UUID=552496e2-92cc-4e0f-87c0-322edc0cb632	/	ext4 noatime,discard,	errors=remount-ro	0	1	# /dev/sda1
# swap was on /dev/sda5 during installation
UUID=5abbcc52-f627-41eb-956f-3f811627ebed	none	swap	sw	0	0	# /dev/sda5

=================== sda1: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
  34.5GB: boot/grub/grub.cfg
  23.5GB: boot/grub/menu.lst
  37.0GB: boot/initrd.img-2.6.38-8-generic
  37.1GB: boot/initrd.img-2.6.38-9-generic
  23.3GB: boot/vmlinuz-2.6.38-8-generic
  36.4GB: boot/vmlinuz-2.6.38-9-generic
  37.1GB: initrd.img
  37.0GB: initrd.img.old
  36.4GB: vmlinuz
  23.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 19 06 84 07  |................|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by cipherboy_loc on 2011-05-08
I would recommend updating to Grub2 and seeing if that fixes your issues. Also, is grub-common for grub2? Or did it also exist for Grub-Legacy (and thus was updated with Grub2)? 


Cipherboy

---

### Post by wilee-nilee on 2011-05-08
@Mike Loubet you need to purge all of the grubs and install one or the other. Your set up will not work with both in the same OS.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Notice that the thread has two methods one from inside the OS and one chrooting from a live cd,. If you use a live cd use only one the same as the install. Personally I find grub2 much easier to deal with.

---

### Post by Mike Loubet on 2011-05-08
@Cipherboy - I really don't know. I had thought I had Grub2 installed. Although, when I purged, grub-efi-amd64 had appeared... It may have been from when I was trying different options when I couldn't get the OS to boot normally.

@wilee-nilee - I am now at step 4, and get the option to install GRUB on two devices. When this option came up when doing the update to 11.04, I installed on both, but I would like to consult before choosing the device:

```
Package configuration                                                           
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474; The grub-pc package is being upgraded. This menu allows you to select     &#9474;  
 &#9474; which devices you'd like grub-install to be automatically run for, if     &#9474;  
 &#9474; any.                                                                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Running grub-install automatically is recommended in most situations, to  &#9474;  
 &#9474; prevent the installed GRUB core image from getting out of sync with GRUB  &#9474;  
 &#9474; modules or grub.cfg.                                                      &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS,    &#9474;  
 &#9474; it is often a good idea to install GRUB to all of them.                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Note: it is possible to install GRUB to partition boot records as well,   &#9474;  
 &#9474; and some appropriate partitions are offered here. However, this forces    &#9474;  
 &#9474; GRUB to use the blocklist mechanism, which makes it less reliable, and    &#9474;  
 &#9474; therefore is not recommended.                                             &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; GRUB install devices:                                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;    [ ] /dev/sda (80026 MB; INTEL_SSDSA2CW080G3)                           &#9474;  
 &#9474;    [ ] - /dev/sda1 (74244 MB; /)                                          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                                  <Ok>                                     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                                
                                                                                
                                                                                
                                                      
```

---

### Post by wilee-nilee on 2011-05-08
sda is where it goes the mbr.

---

### Post by Mike Loubet on 2011-05-08
When i select SDA, I get this:

"You chose not to install GRUB to any devices. If you continue, the boot   &#9474;  
 &#9474; loader may not be properly configured, and when this computer next        &#9474;  
 &#9474; starts up it will use whatever was previously in the boot sector. If      &#9474;  
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474;  
 &#9474; unable to load modules or handle the current configuration file.          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you are already using a different boot loader and want to carry on     &#9474;  
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474;  
 &#9474; boot loader, then you should continue anyway. Otherwise, you should       &#9474;  
 &#9474; install GRUB somewhere.                                                   &#9474;  
 &#9474;                          "

---

### Post by wilee-nilee on 2011-05-08
> **Mike Loubet said:**
> When i select SDA, I get this:

"You chose not to install GRUB to any devices. If you continue, the boot   &#9474;  
 &#9474; loader may not be properly configured, and when this computer next        &#9474;  
 &#9474; starts up it will use whatever was previously in the boot sector. If      &#9474;  
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474;  
 &#9474; unable to load modules or handle the current configuration file.          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you are already using a different boot loader and want to carry on     &#9474;  
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474;  
 &#9474; boot loader, then you should continue anyway. Otherwise, you should       &#9474;  
 &#9474; install GRUB somewhere.                                                   &#9474;  
 &#9474;                          "

Did you hit the tab to actually mark the sda install...if so, your okay. Reboot if you don't get the grub menu, run the bootscript again, and post it.

---

### Post by Mike Loubet on 2011-05-08
I pressed tab, still came up with the same message though..

Rebooted, still got command line :cry:

New bootscript: ```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 126092033 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1   145,009,765   145,009,765  83 Linux
/dev/sda2         145,009,766   156,301,487    11,291,722   5 Extended
/dev/sda5         145,009,767   156,301,487    11,291,721  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        552496e2-92cc-4e0f-87c0-322edc0cb632   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5abbcc52-f627-41eb-956f-3f811627ebed   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,noatime,discard,commit=0,commit=0)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	nodev,noexec,nosuid	0	0
# / was on /dev/sda1 during installation
UUID=552496e2-92cc-4e0f-87c0-322edc0cb632	/	ext4 noatime,discard,	errors=remount-ro	0	1	# /dev/sda1
# swap was on /dev/sda5 during installation
UUID=5abbcc52-f627-41eb-956f-3f811627ebed	none	swap	sw	0	0	# /dev/sda5

=================== sda1: Location of files loaded by Grub: ===================


  37.0GB: boot/initrd.img-2.6.38-8-generic
  37.1GB: boot/initrd.img-2.6.38-9-generic
  23.3GB: boot/vmlinuz-2.6.38-8-generic
  36.4GB: boot/vmlinuz-2.6.38-9-generic
  37.1GB: initrd.img
  37.0GB: initrd.img.old
  36.4GB: vmlinuz
  23.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 19 06 84 07  |................|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Thanks again... And sorry for the lack of progress ](*,)

---

### Post by wilee-nilee on 2011-05-08
It looks like you didn't run the grub reinstall command of
```
sudo apt-get install grub-pc grub-common
```

You got all the grub out but not grub2 back in. Run the chroot again to get this reload command run, you are cleaned up you just need grub actually there.

The post sda or sda1, sda1 would not have fixed this if you added sda1 there, it is asking where does the grub bootloader go.

---

### Post by Mike Loubet on 2011-05-08
I didn't do it from liveCD, I did it from the installed system (ie. followed steps 2-5 on like it says in the guide).

I did run the command before, I just ran it again to make sure GRUB2 was there and it was:

```
mike@Sysem76:~$ sudo apt-get install grub-pc grub-common
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version.
grub-pc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@Sysem76:~$ 

```

Getting a bit frustrated now... haha. Do I have to do it from liveCD then? If so, give me a bit because I have to download an 11.04 image.

---

### Post by wilee-nilee on 2011-05-08
> **Mike Loubet said:**
> I didn't do it from liveCD, I did it from the installed system (ie. followed steps 2-5 on like it says in the guide).

I did run the command before, I just ran it again to make sure GRUB2 was there and it was:

```
mike@Sysem76:~$ sudo apt-get install grub-pc grub-common
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version.
grub-pc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@Sysem76:~$ 

```

Getting a bit frustrated now... haha. Do I have to do it from liveCD then? If so, give me a bit because I have to download an 11.04 image.

Have you run 
sudo update-grub
from the installed OS

You only need the cd if you can't get in normally.

Do thi sin the terminal run the command history, and post the history you have since you have had problems in code tags.

You are missing in the the last bootscipt post this highlighted from my set up.
```
sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   **/boot/grub/grub.cfg **/etc/fstab **/boot/grub/core.img**
```

Yours
```
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab
```

---

### Post by Mike Loubet on 2011-05-08
I made sure to update grub (honestly can't remember if I did before, silly of me not to if i didn't).

Still got the command line boot. Ran the script again and checked the part you said. I'm now getting:

```
Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab
```

without the .img part.

Terminal doesn't like ```
thi sin
```

If there's nothing further I can do, I might try checking the BIOS to see what it's trying to load...

---

### Post by wilee-nilee on 2011-05-08
> **Mike Loubet said:**
> I made sure to update grub (honestly can't remember if I did before, silly of me not to if i didn't).

Still got the command line boot. Ran the script again and checked the part you said. I'm now getting:

```
Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab
```

without the .img part.

Terminal doesn't like ```
**thi sin**
```

If there's nothing further I can do, I might try checking the BIOS to see what it's trying to load...

Hmm in the context of > Do this in the terminal run the command history, and post the history you have since you have had problems in code tags. doesn't this read as **this in**, it is not a command. You have to carefully read and recognise a typing mistake. 

Okay we are way out in La La land now, and going nowhere fast do this.

In the installed ubuntu copy and paste these commands, and run all of them.
```
sudo apt-get purge grub-pc grub-common
```
Then 
```
sudo apt-get install grub-pc grub-common
```
At that choice again of sda or sda1; choose sda hit the tab there or shift whatever marks the sda as being installed to.

The run while still in the OS.
```
sudo update-grub
```
reboot to the grub menu hopefully you should be in shape, unless you have actually removed all the kernels.

---

### Post by Mike Loubet on 2011-05-08
I'm sorry about the typo miss-read, I had no idea that the history command even existed. As you can tell, I'm more of a day-to-day user.

I tried the commands, didn't work. Looked at history and found that it was what I had been doing.

I apologise if you're patience is wearing thin... You have no obligation to continue helping me, and you have been a great help so far, so thanks.

I'm posting the contents of the grub.cfg file, it may help:

```
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
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,71,115; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 552496e2-92cc-4e0f-87c0-322edc0cb632
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by wilee-nilee on 2011-05-08
Have you rebooted to see if you get the grub menu?

I'm a daily user as well I just use it a lot.;)

---

### Post by Mike Loubet on 2011-05-08
We all end up using it alot eventually haha.. In the 2 years I've been using Linux, I've learned more about computers than in the rest of my many years using its proprietary foe. Some have had the good fortune of having used it for longer i guess :)

Anyway, I did reboot.. and still nothing :(. Is there nothing odd in the cfg? I mean, all the kernels are there, it just doesn't want to boot them without me forcibly telling it to...

I did find this odd in the file: ```
set root='(/dev/sda,msdos1)'
```

I don't see what MSDOS has to do with it...

---

### Post by wilee-nilee on 2011-05-08
Yay, see next post.;)

---

### Post by drs305 on 2011-05-08
> **Mike Loubet said:**
> I don't see what MSDOS has to do with it...

It's an MS-DOS partition table, so that is normal.

Reviewing the thread, one thing to note is that during installation you select the MBR to install Grub 2 on by pressing the SPACEBAR. That should put an asterisk next to 'sda', then you TAB to OK and press ENTER. You probably figured that out but I wanted to mention it. If you don't properly select it the BIOS will use whatever was in there previously, even if it's wrong.

I also note you have a -9 kernel, which isn't in the normal repositories yet (at least for me!).

It was a bit hard for me to keep track of what was successful and what wasn't. The 'core.img' file that seemed to be missing is generated by during the initial installation or 'grub-install'. Since it was missing at one point, I'm not sure the entire installation was successful.

At the point of driving you crazy, I would run the entire purge/reinstall again. The reason is that just doing the 'reinstall' part won't  necessarily correct errors if they already exist.

So if you can boot into a normally-running Ubuntu from the grub prompt:
```
sudo apt-get update # As much to ensure you have an Internet connection than to update the repositories.
sudo apt-get purge grub-common  # This will also remove grub-pc
sudo apt-get install grub-pc

```
Again, when you get to the installer, press the SPACEBAR to put an asterisk next to 'sda'. Don't select the partition. TAB to OK, then ENTER.

If you didn't have to use the CD to boot, run "sudo update-grub", although it should have been accomplished during the installation.

See what happens, and if it still doesn't boot, please rerun and post the latest RESULTS.txt

---

### Post by Mike Loubet on 2011-05-08
OK, I don't know if I'm more annoyed than relieved at the fact that it was the space bar all along... haha. It works now though :D

I feel like a bit of an idiot... Although I swear I've never had to press space before in these circumstances.

Thank you all oh-so much, you've saved me a massive headache and helped me learn a bit about GRUB ;)

I'm still in the dark though as to WHY the upgrade messed up my GRUB. Is there anything I can contribute as a bug report or the like?

---

### Post by drs305 on 2011-05-08
> **Mike Loubet said:**
> I'm still in the dark though as to WHY the upgrade messed up my GRUB. Is there anything I can contribute as a bug report or the like?

Here is what I suspect happened: When you upgraded, since you didn't know about the SPACEBAR it updated the Grub folder/files but didn't update the MBR contents. 

The update from Maverick to Natty included an upgrade from Grub 1.98 to Grub 1.99. There are some pretty significant changes, and it appears that what is written in the MBR must be compatible with the contents of the Grub folders. So you were trying to use Grub 1.98 MBR instructions with Grub 1.99 contents, which failed.

A note to the helpers: It's something to keep in mind. Using a compatible CD for repair work is going to be important for this upgrade. It doesn't appear you are going to be able to use the "grub-install" command from a different release's CD if one of the two (CD & OS) is Natty.

---

### Post by Mike Loubet on 2011-05-08
Agreed, it all makes sense now :P.

It would add user-friendliness just to have ENTER to make a selection (as I previously recall it to be) rather than SPACEBAR>TAB>ENTER... Might suggest it.

OK, well thanks again to all, and I show now mark this thread as SOLVED. :)

---

