---
title: "An incredible mess (Machine wont boot)"
date: 2011-03-02
forum: General Help
---

### Post by The Mickmeister on 2011-03-02
I am having issues with GRUB. I have a dual boot installation, on one partition I have Windows 7, and on the other I have Ubuntu (10.04?). Previously I was having trouble with a Vista installation, so upgraded to Windows 7 in the hope that it would solve my problems. Upon upgrading I realised that it hadn't, and decided to perform a new installation. As you're probably aware, once Windows 7 was installed it replaced GRUB with Windows Boot Manager. 

At this point I could no longer access Ubuntu, and decided that I didn't want to use GRUB anymore, so I set about creating an entry for Ubuntu in the Master Boot Record so that I could switch between the two partitions. To do this I downloaded a 3rd party Windows application called EasyBCD. I added an entry named 'Linux' and then rebooted as instructed. Upon rebooting there was only one option presented by Windows Boot Manager, the option that I had previously named 'Linux'. 

So I could no longer boot into Windows. After selecting the Linux option GRUB appeared and displayed my 4 kernels along with an additional entry named 'Windows Vista' - this was the entry that I used to boot into my old Vista installation before it began causing me problems. I attempted to use this entry (/dev/sda1 at the time) to boot into Windows 7 (currently /dev/sda1) in the hope it would be working. Instead the screen went completely blank and then brought me back to the GRUB menu. 

I had no option but to boot into Ubuntu and seek advice on the Ubuntu IRC channel on Freenode. Speaking with a few people on here, I concluded that I would need a Windows recovery disc however I didn't have one available, somebody suggested downloading an MBR application (I don't know what it was called but I installed it by doing 'sudo apt-get install something') and running it in an attempt to repair the MBR in Windows. I rebooted and then couldn't access either partition. 

I received an error message similar to "\NST\NeoGrub.mbr. Status 0xc000000f" from Windows Boot Manager. I am now using a Live CD in order to seek help. So can anybody help? You might find the ouput from this startup script useful in assisting me troubleshoot - [http://pastebin.com/XpWWS5z3](http://pastebin.com/XpWWS5z3)

Thanks! :P

---

### Post by houseworkshy on 2011-03-02
Whew.  As far as typing a few commands and sorting it out I'm not sure enough to give advice.  Get your work backed up anyway, if you have only one cd/dvd drive then use a small linux which can be loaded to ram and has burner software included ( Puppy linux is excellent for this sort of thing )
Looking at that output I know that I'm out of my depth.  If you don't get "just enter these commands" type advice ( and if you wait I hope you do as I'm sure the knowlage is out there and your computer is not broken it's just software ) a format and fresh start would work but you'd have to put windows in first as Ubuntu recognises windows and will make a duel boot entry for it but NOT visa versa.
Just call this an elaborate bump, good luck.

---

### Post by Hedgehog1 on 2011-03-02
My goodness - I think you have hit a new level of pain...

From the terminal on the live CD:

```
sudo grub-install --recheck /dev/sda
```

Then you should (we all hope) get the Grub menu and boot into Windows and Ubuntu.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-02
Here is the complete page, in case we need it:

[http://ubuntuforums.org/showthread.php?t=1581099&highlight=grub+purge]("http://ubuntuforums.org/showthread.php?t=1581099&highlight=grub+purge")

And your output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   439,812,087   439,810,040   7 HPFS/NTFS
/dev/sda2         439,827,570   440,229,194       401,625  83 Linux
/dev/sda3         440,229,195   625,137,344   184,908,150   5 Extended
/dev/sda5         619,080,903   625,137,344     6,056,442  82 Linux swap / Solaris
/dev/sda6         611,707,131   619,080,839     7,373,709  82 Linux swap / Solaris
/dev/sda7         440,229,321   611,707,004   171,477,684  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1007 MB, 1007681536 bytes
255 heads, 63 sectors/track, 122 cylinders, total 1968128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,968,127     1,968,065   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5CC0D933C0D913DC                       ntfs                                     
/dev/sda2        a5f665f3-ce4b-4a14-a452-6c5bc6cf429b   ext3       /boot                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        6e43965d-e470-41e1-8697-e1c94942a043   swap                                     
/dev/sda6        3e8d5eff-c08f-4ba2-b398-96a0d0cc3352   swap                                     
/dev/sda7        4f7805fb-2d00-49a9-9eb1-9962f9ced764   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A9C2-F8AE                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/DOG_POUND         udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)
/dev/sda7        /mnt                     ext4       (rw)


============================= sda2/grub/menu.lst: =============================

default 0
timeout 10

title Ubuntu
root (hd0,1)
kernel /vmlinuz-2.6.25-14.fc9.x86_64 root=/dev/sda4
initrd /initrd-2.6.25-14.fc9.x86_64.img

title Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

============================= sda2/grub/grub.cfg: =============================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set bd87999e-fcd5-44f9-b7c6-6ed84dd7720b
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
menuentry "Ubuntu, Linux 2.6.25-14.fc9.x86_64" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set a5f665f3-ce4b-4a14-a452-6c5bc6cf429b
	linux	/vmlinuz-2.6.25-14.fc9.x86_64 root=UUID=bd87999e-fcd5-44f9-b7c6-6ed84dd7720b ro   quiet splash
	initrd	/initrd-2.6.25-14.fc9.x86_64.img
}
menuentry "Ubuntu, Linux 2.6.25-14.fc9.x86_64 (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set a5f665f3-ce4b-4a14-a452-6c5bc6cf429b
	linux	/vmlinuz-2.6.25-14.fc9.x86_64 root=UUID=bd87999e-fcd5-44f9-b7c6-6ed84dd7720b ro single 
	initrd	/initrd-2.6.25-14.fc9.x86_64.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda2: Location of files loaded by Grub: ===================


 225.2GB: grub/core.img
 225.2GB: grub/grub.cfg
 225.2GB: grub/menu.lst
 225.2GB: grub/stage2
 225.2GB: initrd-2.6.25-14.fc9.x86_64.img
 225.2GB: vmlinuz-2.6.25-14.fc9.x86_64

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4f7805fb-2d00-49a9-9eb1-9962f9ced764

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

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.32-28-generic
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.10, kernel 2.6.32-28-generic (recovery mode)
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.32-28-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro  single
initrd		/boot/initrd.img-2.6.32-28-generic

title		Ubuntu 10.10, kernel 2.6.32-21-generic
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.10, kernel 2.6.32-21-generic (recovery mode)
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.10, kernel 2.6.31-14-generic
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.10, kernel 2.6.31-14-generic (recovery mode)
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		4f7805fb-2d00-49a9-9eb1-9962f9ced764
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows Vista&#8243; {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 4f7805fb-2d00-49a9-9eb1-9962f9ced764
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

echo "Adding Windows OS to Grub 2 menu"
       cat << EOF
       menuentry "Microsoft Windows Vista" {
       set root=(hd0,1)         
       makeactive
       chainloader +1
       }
       EOF
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=4f7805fb-2d00-49a9-9eb1-9962f9ced764 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6e43965d-e470-41e1-8697-e1c94942a043 none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=3e8d5eff-c08f-4ba2-b398-96a0d0cc3352 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 225.5GB: boot/grub/core.img
 226.7GB: boot/grub/grub.cfg
 225.5GB: boot/grub/menu.lst
 236.4GB: boot/initrd.img-2.6.31-14-generic
 236.7GB: boot/initrd.img-2.6.32-21-generic
 247.5GB: boot/initrd.img-2.6.32-28-generic
 273.5GB: boot/initrd.img-2.6.35-25-generic
 228.4GB: boot/vmlinuz-2.6.31-14-generic
 234.5GB: boot/vmlinuz-2.6.32-21-generic
 256.9GB: boot/vmlinuz-2.6.32-28-generic
 258.4GB: boot/vmlinuz-2.6.35-25-generic
 273.5GB: initrd.img
 247.5GB: initrd.img.old
 258.4GB: vmlinuz
 256.9GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
```

---

### Post by Hedgehog1 on 2011-03-02
> **The Mickmeister said:**
> I am having issues with GRUB. I have a dual boot installation...

Mickmeister,

Are you operational yet? Or do you need more help?  Let us know.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-02
> **houseworkshy said:**
> ...Just call this an elaborate bump, good luck.

houseworkshy,

Thanks for bumping this yesterday.  It really needed attention!

:popcorn:

---

