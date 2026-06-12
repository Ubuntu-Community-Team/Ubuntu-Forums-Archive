---
title: "Windows not showing in grub"
date: 2010-11-07
forum: General Help
---

### Post by adamaze on 2010-11-07
i just installed ubuntu and windows is not showing up in grub (it actually doesnt even go to grub, just straight to ubuntu. 

i read somewhere that it would be helpful if i ran a boot_info_ script, so i attached that.

could someone help me rebuild grub? 

thanks

---

### Post by dcstar on 2010-11-07
> **adamaze said:**
> i just installed ubuntu and windows is not showing up in grub (it actually doesnt even go to grub, just straight to ubuntu. 

i read somewhere that it would be helpful if i ran a boot_info_ script, so i attached that.

could someone help me rebuild grub? 

thanks

```
sudo update-grub
```

---

### Post by adamaze on 2010-11-07
yeah, i already did that, but when i look at /boot/grub/menu.lst , windows is not there

thanks though

---

### Post by Quackers on 2010-11-07
Your boot script in code tags

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   668,245,226   668,243,179   7 HPFS/NTFS
/dev/sda2         668,246,014   976,771,071   308,525,058   5 Extended
/dev/sda5         668,246,016   976,584,703   308,338,688  83 Linux
/dev/sda6         976,586,752   976,771,071       184,320  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E0509E8F509E6C52                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        be83000a-937e-4c8a-9d5c-161adafbfd5b   ext4                                     
/dev/sda6        764a235d-9bc5-40bd-a516-c1123b1d3b77   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1        /media/E0509E8F509E6C52  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
# kopt=root=UUID=be83000a-937e-4c8a-9d5c-161adafbfd5b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=be83000a-937e-4c8a-9d5c-161adafbfd5b

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

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		be83000a-937e-4c8a-9d5c-161adafbfd5b
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=be83000a-937e-4c8a-9d5c-161adafbfd5b ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		be83000a-937e-4c8a-9d5c-161adafbfd5b
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=be83000a-937e-4c8a-9d5c-161adafbfd5b ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		be83000a-937e-4c8a-9d5c-161adafbfd5b
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		be83000a-937e-4c8a-9d5c-161adafbfd5b
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set be83000a-937e-4c8a-9d5c-161adafbfd5b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set be83000a-937e-4c8a-9d5c-161adafbfd5b
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be83000a-937e-4c8a-9d5c-161adafbfd5b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=be83000a-937e-4c8a-9d5c-161adafbfd5b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be83000a-937e-4c8a-9d5c-161adafbfd5b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=be83000a-937e-4c8a-9d5c-161adafbfd5b ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be83000a-937e-4c8a-9d5c-161adafbfd5b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set be83000a-937e-4c8a-9d5c-161adafbfd5b
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
UUID=be83000a-937e-4c8a-9d5c-161adafbfd5b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=764a235d-9bc5-40bd-a516-c1123b1d3b77 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 423.8GB: boot/grub/core.img
 423.8GB: boot/grub/grub.cfg
 454.0GB: boot/grub/menu.lst
 343.0GB: boot/initrd.img-2.6.35-22-generic
 423.8GB: boot/vmlinuz-2.6.35-22-generic
 343.0GB: initrd.img
 423.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  cc 9a da 82 17 3f 5b 6e  6a 10 d5 91 d6 c9 7e 0e  |.....?[nj.....~.|
00000010  b1 4d 13 f2 ab 43 91 0b  48 b9 43 2e 03 94 6b 0b  |.M...C..H.C...k.|
00000020  7e 9e 37 87 81 0c 08 05  e8 de b3 92 87 e5 2d 8c  |~.7...........-.|
00000030  55 23 9b 37 45 0c 52 48  84 a6 0c 5c 64 12 4b d6  |U#.7E.RH...\d.K.|
00000040  af 69 ca 63 e4 b9 1d 51  b2 1b 2a 6c 9c 27 6a c7  |.i.c...Q..*l.'j.|
00000050  2b 21 5c e0 f2 76 78 66  c9 51 2a 33 53 e5 63 6e  |+!\..vxf.Q*3S.cn|
00000060  85 6e 69 b3 90 4a 5b a5  e5 63 dd ab ea 5e 45 7c  |.ni..J[..c...^E||
00000070  a5 a0 b0 39 37 8e aa e3  74 19 0d 36 29 2c b4 3b  |...97...t..6),.;|
00000080  c4 0a 8f 26 3a 00 16 8a  1f f7 76 6b 62 68 ae 81  |...&:.....vkbh..|
00000090  d2 7b 72 33 4a 60 35 1a  e3 db dc 9a 44 1e 15 7a  |.{r3J`5.....D..z|
000000a0  c5 c1 0b 5e 15 e4 b2 1a  f7 04 2c 03 fa 17 50 ed  |...^......,...P.|
000000b0  27 39 7a 95 3c c9 fd 08  cc 6d 6f d0 12 71 3e dd  |'9z.<....mo..q>.|
000000c0  a1 ef a7 e1 c0 30 b4 22  40 e0 ad 90 89 4e f6 12  |.....0."@....N..|
000000d0  be 32 01 cb bd f3 37 4d  2a 65 b3 9b d4 98 e1 84  |.2....7M*e......|
000000e0  0f 23 14 2c 31 fd 84 ee  15 01 85 6b 01 be d4 fb  |.#.,1......k....|
000000f0  bf 21 66 74 e6 0e 83 c7  55 3f f1 83 34 93 6d 50  |.!ft....U?..4.mP|
00000100  9f 6c 6c 88 01 eb 3a 12  ed b1 a6 5c 09 87 39 19  |.ll...:....\..9.|
00000110  18 4d 7f d2 7d 71 82 7d  bc 1c 79 b6 fd cc bc d5  |.M..}q.}..y.....|
00000120  90 02 4a c2 6d ce 5a 86  41 ea 8b 8a c1 e5 36 5b  |..J.m.Z.A.....6[|
00000130  15 22 f1 bd 6b 19 f7 56  da c2 d8 14 16 9c a3 67  |."..k..V.......g|
00000140  52 94 70 55 72 17 c7 1a  c3 41 82 f9 b4 98 cb 98  |R.pUr....A......|
00000150  3b af bf b4 1a d1 e9 fe  c6 ce 66 ac a6 bd 12 44  |;.........f....D|
00000160  aa ba cf e0 a9 6f f7 ac  5c e7 a3 f5 ac 68 49 27  |.....o..\....hI'|
00000170  a4 6e d1 d7 b5 c8 80 47  c0 e6 1a 2b b6 5e de 53  |.n.....G...+.^.S|
00000180  39 03 3d 54 3c f1 a0 1a  a5 5f 88 ef 96 b4 59 94  |9.=T<...._....Y.|
00000190  8a 86 6e a2 3f 49 6d aa  91 5a 19 c2 48 bf 7f 8f  |..n.?Im..Z..H...|
000001a0  d7 e1 b1 e1 0b 0f a5 6c  fb db 3c 31 02 e4 0e 12  |.......l..<1....|
000001b0  52 50 85 c8 ac 43 a9 ea  e2 4f 70 50 be 41 00 fe  |RP...C...OpP.A..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 60 12 00 fe  |............`...|
000001d0  ff ff 05 fe ff ff 02 e0  60 12 00 d8 02 00 00 00  |........`.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2010-11-07
Have you by any chance deleted a partition (recovery maybe)?
It seems you have Windows 7 on sda1, but 2 boot files are missing.
You have half of grub legacy and half of grub2 installed.

Do you have a Windows repair disc?

---

### Post by adamaze on 2010-11-07
yeah... i did some wacky things when installing...I started off and installed ubuntu normally, but it never booted to grub, just back into windows. I removed the secondary drive i had in the computer (it was set as a slave) and then grub came up, but no windows.

 i ended up with two installations of ubuntu somehow at one point, then i figured i would just install again and delete the ubuntu partitions i have made before, extend the windows one to take up the full drive and try the simple install of "install side by side with another OS" (all of which i did)


is it salvageable?

thanks

---

### Post by Kr0nZ on 2010-11-07
i had this problem once before, it was awhile ago but i think i fixed it by repairing the windows boot uding the windows cd then it booted into windows using the windows loader, then i used a linux live disk to reinstall grub

---

### Post by Quackers on 2010-11-07
Yes it's salvageable. Kr0nz has the answer.
What I would do is boot from your windows repair disk and run startup repair THREE times - rebooting in between each run. On the third run it should find your W7 install and offer you the chance to add it to the boot menu (or similar). Answer Y for yes and reboot. Check W7 boots ok.
Then boot from your Ubuntu Live CD and go to the link below and follow the directions drs305 gives for "purging and re-installing grub2".
After running his commands, all should be good - hopefully :-)

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by adamaze on 2010-11-07
i ran startup repair thrice to no avail. it still just boots right into ubuntu. the last time i ran startup repair, it told me that there were no errors.

any ideas?

thanks for the help so far.

---

### Post by Quackers on 2010-11-07
Boot from your Windows repair disc and select the command prompt then enter
```
bootrec.exe /fixmbr
bootrec.exe /fixboot
```
Then reboot and check that Windows boots ok.
Then I would suggest that you will need to purge grub/grub2 and reinstall grub2 following drs305's guide in my last post.

---

