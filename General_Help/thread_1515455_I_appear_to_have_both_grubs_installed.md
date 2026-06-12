---
title: "I appear to have both grubs installed"
date: 2010-06-22
forum: General Help
---

### Post by nazoreth on 2010-06-22
hello,

long time reader, first time poster

i appear to have both grubs installed

under /boot/grub i have both a menu.lst and a grub.cfg


im booting fine, can update-grub fine, my only issue is that i can't remove old kernels and update the correct grub

my menu.lst doesn't show the old kernel so i can only assume im booting with grub2 but can only update-grub for grub(1)


any ideas? it's a minor issue now but i'm worried it will have wider consequences in time


many thanks

naz

---

### Post by WorMzy on 2010-06-22
Uninstall grub legacy then reinstall grub2 to fix anything that grub legacy removed. It won't change which bootloader is called from the MBR.

---

### Post by nazoreth on 2010-06-22
hmm

can i simply do this with - 

sudo aptitude uninstall grub

sudo aptitude reinstall grub-pc

?

thanks for replying


edit - also curiously grub-pc appears to not be installed, i thought that was the synaptic package for grub2?

---

### Post by WorMzy on 2010-06-22
As did I. Perhaps it's the other way around.

Could you open a terminal and run "grub --version"? That'll tell you which version is being used. 0.97 means grub legacy, 1.98 means grub 2.

---

### Post by nazoreth on 2010-06-22
yeah i'm getting confused,

i already checked the version and it came back with GNU Grub 0.97 which, like you say, is the legacy


i still seem to have the grub.cfg though and im pretty sure lucid is meant to use grub2

about a week ago, in trying to remove my old kernel, i read the method for the wrong grub and tried to edit menu.lst (which in theory wouldn't have existed if i was on grub2) could i possibly have created a menu.lst in the process and somehow installed grub legacy....??? no that just sounds stupid when i read it back to myself but hey

---

### Post by WorMzy on 2010-06-22
Yeah, Lucid uses Grub2 by default, but if you upgraded from 9.10 (or earlier) it may have installed grub2 despite grub legacy already being installed; I think grub legacy would still be used though, because the upgrade wouldn't have written a new MBR (as far as I know). Do you have any other Linux installations on your hard drive(s) which might be used for booting?

Can you download and run this: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Post the text it generates here, it'll (hopefully) confirm which version of grub is being called at boot time.

---

### Post by nazoreth on 2010-06-22
nope its a fresh install, i managed to destroy my pc about a month ago whilst messing around with partitions

i formatted both my hard drives to ntfs, installed windows 7, then installed ubuntu alongside it so all should be fresh and neat


im using ssh on my pc at the moment but will run that script when i get home in an hour and will report back.

many many thanks for your help

---

### Post by WorMzy on 2010-06-22
You installed Ubuntu on it's own partition, right? Or did you install it using the Windows based installer?

---

### Post by nazoreth on 2010-06-22
yep used ubuntu disk to create a partition in the first hard drive -

2 hard drives

number 1 is 70% ntfs partition with windows
                  30% ext4 partition with ubuntu

number 2 is just ntfs with data

---

### Post by nazoreth on 2010-06-22
not sure how to attach so here goes -


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   224,445,717   224,238,870   7 HPFS/NTFS
/dev/sda3         224,446,462   312,580,095    88,133,634   5 Extended
/dev/sda5         224,446,464   308,877,311    84,430,848  83 Linux
/dev/sda6         308,879,360   312,580,095     3,700,736  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   156,299,263   156,297,216   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4CECE9E0ECE9C474                       ntfs       System Reserved               
/dev/sda2        167CF69C7CF675B9                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e98481ef-492d-4cd5-a2a4-547ada69f092   ext4                                     
/dev/sda6        efcb45f2-2b13-4fea-ac7a-7b075e23b60e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        00EAE6EBEAE6DBC2                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/00EAE6EBEAE6DBC2  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
# kopt=root=UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e98481ef-492d-4cd5-a2a4-547ada69f092

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		e98481ef-492d-4cd5-a2a4-547ada69f092
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		e98481ef-492d-4cd5-a2a4-547ada69f092
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Chainload into GRUB 2
root		e98481ef-492d-4cd5-a2a4-547ada69f092
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		e98481ef-492d-4cd5-a2a4-547ada69f092
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
search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
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
search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set e98481ef-492d-4cd5-a2a4-547ada69f092
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4cece9e0ece9c474
	chainloader +1
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
UUID=e98481ef-492d-4cd5-a2a4-547ada69f092 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=efcb45f2-2b13-4fea-ac7a-7b075e23b60e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 145.1GB: boot/grub/core.img
 132.2GB: boot/grub/grub.cfg
 149.4GB: boot/grub/menu.lst
 145.1GB: boot/initrd.img-2.6.32-22-generic
 115.4GB: boot/vmlinuz-2.6.32-22-generic
 145.1GB: initrd.img
 115.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  55 48 89 e5 48 83 ec 30  48 89 5d d8 4c 89 65 e0  |UH..H..0H.].L.e.|
00000010  4c 89 6d e8 4c 89 75 f0  4c 89 7d f8 e8 00 00 00  |L.m.L.u.L.}.....|
00000020  00 48 8b 07 4c 8b 67 58  85 f6 48 89 fb 4c 8b 68  |.H..L.gX..H..L.h|
00000030  30 78 73 41 0f b7 44 24  28 39 47 6c 72 64 48 8b  |0xsA..D$(9GlrdH.|
00000040  87 88 00 00 00 49 03 45  08 85 d2 49 89 04 24 75  |.....I.E...I..$u|
00000050  1f 4c 89 e7 e8 00 00 00  00 48 8b 5d d8 4c 8b 65  |.L.......H.].L.e|
00000060  e0 4c 8b 6d e8 4c 8b 75  f0 4c 8b 7d f8 c9 c3 90  |.L.m.L.u.L.}....|
00000070  48 8b 07 48 8d 77 10 48  8b 50 30 48 8d 47 18 48  |H..H.w.H.P0H.G.H|
00000080  c7 47 10 00 00 00 00 48  c7 47 28 00 00 00 00 48  |.G.....H.G(....H|
00000090  89 47 18 48 89 47 20 48  8b 7a 30 e8 00 00 00 00  |.G.H.G H.z0.....|
000000a0  eb b7 0f 0b eb fe 66 41  83 7c 24 28 00 0f 1f 00  |......fA.|$(....|
000000b0  74 49 4d 8b 74 24 48 45  31 ff 49 8b 3e 48 85 ff  |tIM.t$HE1.I.>H..|
000000c0  75 1a eb 56 0f 1f 40 00  45 89 fe 49 c1 e6 04 4d  |u..V..@.E..I...M|
000000d0  03 74 24 48 49 8b 3e 48  85 ff 74 3e 49 8b 75 20  |.t$HI.>H..t>I.u |
000000e0  41 83 c7 01 e8 00 00 00  00 49 c7 06 00 00 00 00  |A........I......|
000000f0  41 0f b7 44 24 28 41 39  c7 72 cd 4c 89 e7 e8 00  |A..D$(A9.r.L....|
00000100  00 00 00 c7 83 84 00 00  00 fb ff ff ff 48 89 df  |.............H..|
00000110  e8 bb fb ff ff e9 3f ff  ff ff 0f 0b eb fe 66 90  |......?.......f.|
00000120  55 48 89 e5 e8 00 00 00  00 31 c0 48 85 c9 48 89  |UH.......1.H..H.|
00000130  4e 20 48 89 56 28 c7 46  30 00 00 00 00 c7 46 34  |N H.V(.F0.....F4|
00000140  00 00 00 00 74 04 0f b7  41 2a 89 46 38 31 c0 48  |....t...A*.F81.H|
00000150  85 d2 74 04 0f b7 42 2a  89 46 3c 4c 03 47 68 48  |..t...B*.F<L.GhH|
00000160  8d 7e 08 c7 06 00 00 00  00 4c 89 46 40 48 c7 c6  |.~.......L.F@H..|
00000170  00 00 00 00 e8 00 00 00  00 c9 c3 0f 1f 44 00 00  |.............D..|
00000180  55 48 89 e5 48 83 ec 20  48 89 5d e8 4c 89 65 f0  |UH..H.. H.].L.e.|
00000190  4c 89 6d f8 e8 00 00 00  00 48 8b 7f 18 83 fe 8d  |L.m......H......|
000001a0  89 f3 4c 8b 2f 49 8b 45  d0 4d 8d 65 d0 48 8b 40  |..L./I.E.M.e.H.@|
000001b0  30 74 45 48 8b 70 18 8b  40 74 48 29 c7 e8 00 fe  |0tEH.p..@tH)....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 08 05 00 fe  |...........P....|
000001d0  ff ff 05 fe ff ff 02 50  08 05 00 80 38 00 00 00  |.......P....8...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 



so curiously it appears to have both grubs like i said, fun huh?

---

### Post by nazoreth on 2010-06-22
so it seems im using grub 2, but it claims to have installed grub legacy

all i really want to do is figure out how to update-grub on the grub.cfg to remove old kernel entry


thanks endlessly

---

### Post by WorMzy on 2010-06-22
Oh wow, I've never seen anything like this before. The script reports that you're using Grub2, and I'm inclined to believe that over what grub --version is reporting. I'm not sure why Synaptic is reporting that Grub2 isn't installed, but I'm going to assume that at some point you accidentally installed Grub, and for reasons unknown that decided to leave behind the grub2 files, but mark the grub2 package as uninstalled.

I think the best course of action would be to purge both grub and grub 2, then install grub 2, and then reinstall grub2 to the MBR just in case.

After you've installed grub2, run ```
sudo grub-install /dev/sda
``` and then ```
sudo grub-install /dev/sdb
``` (Unless you know which hard disk is first in your BIOS' boot list)

After that running "sudo update-grub" should work fine.


Oh, and just in case something goes horribly horribly wrong and you can't boot afterwards: Don't panic. Your Ubuntu partition is fine. You just need to boot a Live CD and fix grub (again).

---

### Post by nazoreth on 2010-06-22
ahh glad ive managed to break things like never before

install grub2 with -

sudo apt-get install grub-pc

right?

many thanks

---

### Post by nazoreth on 2010-06-22
whahey!

that worked perfectly

just in case someone needs to reference this thread or send it to grub or something it was fixed with the following -

sudo aptitude purge grub
sudo aptitude purge grub-common
sudo apt-get install grub-pc
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
sudo update-grub

reboot and cross fingers

done




now i only have one version of grub and no more old kernels

thanks so so much for your help

hope england win tomorrow

---

### Post by WorMzy on 2010-06-22
Glad to see it all worked out fine. :)

Fingers crossed, eh? In any case, at least we can't get much worse than France. :P

---

