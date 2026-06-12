---
title: "Disc drive UUID = xxx not ready yet or unavailable"
date: 2012-06-10
forum: General Help
---

### Post by wrknight on 2012-06-10
Upgraded to ubuntu 12.04 (64 bit) from 11.10.  On boot up, there is a long delay with the message stating "The disc drive UUID=    is not ready yet or is not available".  According to fstab, the UUID listed belongs to the swap file on sda2.

A second delay of about 2 minutes gets the message "Waiting for network configuration."  After waiting for both delays, the system will boot with the message "Booting without full network configuration".  After booting, system seems to run OK.  

Total boot time is nearly 5 minutes.  System is intel dual core E2200 running 2.2 GHz with 4 GB RAM   

After upgrade, there was no grub.cfg file in /boot/grub directory.  Used "grub-mkconfig -o /boot/grub/grub.cfg"    to make a grub file and mounted with "grub-install /dev/sda".  No change.

Any ideas please?

---

### Post by wilee-nilee on 2012-06-10
> **wrknight said:**
> Upgraded to ubuntu 12.04 (64 bit) from 11.10.  On boot up, there is a long delay with the message stating "The disc drive UUID=    is not ready yet or is not available".  According to fstab, the UUID listed belongs to the swap file on sda2.

A second delay of about 2 minutes gets the message "Waiting for network configuration."  After waiting for both delays, the system will boot with the message "Booting without full network configuration".  After booting, system seems to run OK.  

Total boot time is nearly 5 minutes.  System is intel dual core E2200 running 2.2 GHz with 4 GB RAM   

After upgrade, there was no grub.cfg file in /boot/grub directory.  Used "grub-mkconfig -o /boot/grub/grub.cfg"    to make a grub file and mounted with "grub-install /dev/sda".  No change.

Any ideas please?

You might run the bootscript, it will show the grub you do have and the fstab info.
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

You will see a reults.txt in home to look through, post it if needed

---

### Post by wrknight on 2012-06-10
Ran bootinfoscript as instructed.  Tried to attach RESULTS.txt, but file size exceeds limit.  Results indicated that Grub was looking for the stage2 file but couldn't find it.  There is a file named stage2 in /boot/grub/.

Here is part of the file.  

=====================================================================

   File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v) is installed in the boot sector of 
                       sda1 and looks at sector 1181615 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

---

### Post by wilee-nilee on 2012-06-10
> **wrknight said:**
> Ran bootinfoscript as instructed.  Tried to attach RESULTS.txt, but file size exceeds limit.  Results indicated that Grub was looking for the stage2 file but couldn't find it.  There is a file named stage2 in /boot/grub/.

Here is part of the file.  

=====================================================================

   File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v) is installed in the boot sector of 
                       sda1 and looks at sector 1181615 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

You can highlight all the text and copy and paste post it.

When you do before submitting the reply highlight all that text and click on the # in the reply panel.

This wraps the text in code tags so it is easier to read.

Just from this little bit of text I see grub legacy and grub2, I suspected this all the text is needed though to really help.

---

### Post by wrknight on 2012-06-10
RESULTS.txt content



  ```
                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v) is installed in the boot sector of 
                       sda1 and looks at sector 1181615 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   480,423,824   480,423,762  83 Linux
/dev/sda2         480,423,825   488,392,064     7,968,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        589f4805-7b81-497a-acaa-694b4b85f93e   ext3       
/dev/sda2                                               swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 11.10, kernel 3.0.0-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-3.0.0-12-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-3.0.0-12-generic

title		Ubuntu 11.10, kernel 2.6.38-8-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic
quiet

title		Ubuntu 11.10, kernel 2.6.38-8-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.10, kernel 2.6.34-020634-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.34-020634-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.34-020634-generic
quiet

title		Ubuntu 11.10, kernel 2.6.34-020634-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.34-020634-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.34-020634-generic

title		Ubuntu 11.10, kernel 2.6.32-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 11.10, kernel 2.6.32-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 11.10, kernel 2.6.31-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 11.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 11.10, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 11.10, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 11.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 11.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 11.10, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 11.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 11.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 11.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 11.10, memtest86+
root		(hd0,0)
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
true
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'GNU/Linux, with Linux 3.2.0-23-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'GNU/Linux, with Linux 3.2.0-23-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
submenu "Previous Linux versions" {
menuentry 'GNU/Linux, with Linux 3.0.0-12-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'GNU/Linux, with Linux 3.0.0-12-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'GNU/Linux, with Linux 2.6.38-8-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'GNU/Linux, with Linux 2.6.38-8-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'GNU/Linux, with Linux 2.6.34-020634-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.34-020634-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.34-020634-generic
}
menuentry 'GNU/Linux, with Linux 2.6.34-020634-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.34-020634-generic ...'
	linux	/boot/vmlinuz-2.6.34-020634-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.34-020634-generic
}
menuentry 'GNU/Linux, with Linux 2.6.32-21-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'GNU/Linux, with Linux 2.6.32-21-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'GNU/Linux, with Linux 2.6.31-14-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'GNU/Linux, with Linux 2.6.31-14-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'GNU/Linux, with Linux 2.6.28-11-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry 'GNU/Linux, with Linux 2.6.28-11-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.28-11-generic ...'
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry 'GNU/Linux, with Linux 2.6.27-7-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.27-7-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.27-7-generic
}
menuentry 'GNU/Linux, with Linux 2.6.27-7-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.27-7-generic ...'
	linux	/boot/vmlinuz-2.6.27-7-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.27-7-generic
}
menuentry 'GNU/Linux, with Linux 2.6.24-16-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.24-16-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.24-16-generic
}
menuentry 'GNU/Linux, with Linux 2.6.24-16-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.24-16-generic ...'
	linux	/boot/vmlinuz-2.6.24-16-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-16-generic
}
menuentry 'GNU/Linux, with Linux 2.6.22-14-generic' --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   
	initrd	/boot/initrd.img-2.6.22-14-generic
}
menuentry 'GNU/Linux, with Linux 2.6.22-14-generic (recovery mode)' --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.22-14-generic ...'
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.22-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=589f4805-7b81-497a-acaa-694b4b85f93e /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda2
UUID=50287a93-4a31-4587-8e98-e155dc5bd544 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.574065685 = 0.616398336    boot/grub/grub.cfg                             3
   1.141833782 = 1.226034688    boot/grub/menu.lst                             1
   0.548961163 = 0.589442560    boot/grub/stage2                              14
   3.742286205 = 4.018249216    boot/initrd.img-2.6.22-14-generic              3
   3.759742260 = 4.036992512    boot/initrd.img-2.6.22-14-generic.bak          3
   3.771960735 = 4.050112000    boot/initrd.img-2.6.24-16-generic              3
   3.749534130 = 4.026031616    boot/initrd.img-2.6.24-16-generic.bak          3
   0.856063366 = 0.919191040    boot/initrd.img-2.6.27-7-generic              121
   3.916934490 = 4.205776384    boot/initrd.img-2.6.28-11-generic             122
   1.581634045 = 1.698266624    boot/initrd.img-2.6.31-14-generic             55
   1.616641521 = 1.735855616    boot/initrd.img-2.6.32-21-generic             121
   1.223445415 = 1.313664512    boot/initrd.img-2.6.34-020634-generic         112
   1.373759747 = 1.475063296    boot/initrd.img-2.6.38-8-generic              111
   1.364890575 = 1.465540096    boot/initrd.img-3.0.0-12-generic              176
   1.589992046 = 1.707240960    boot/initrd.img-3.2.0-23-generic              327
   3.761474133 = 4.038852096    boot/vmlinuz-2.6.22-14-generic                 2
   3.763236523 = 4.040744448    boot/vmlinuz-2.6.24-16-generic                 2
   0.658469677 = 0.707026432    boot/vmlinuz-2.6.27-7-generic                  2
   0.748462200 = 0.803655168    boot/vmlinuz-2.6.28-11-generic                 2
   0.525809765 = 0.564583936    boot/vmlinuz-2.6.31-14-generic                22
   0.950587749 = 1.020685824    boot/vmlinuz-2.6.32-21-generic                56
   1.745540142 = 1.874259456    boot/vmlinuz-2.6.34-020634-generic             4
   0.563910961 = 0.605494784    boot/vmlinuz-2.6.38-8-generic                 136
   1.302104473 = 1.398124032    boot/vmlinuz-3.0.0-12-generic                 117
   0.993857861 = 1.067146752    boot/vmlinuz-3.2.0-23-generic                 303
   1.589992046 = 1.707240960    initrd.img                                    327
   1.364890575 = 1.465540096    initrd.img.old                                176
   0.993857861 = 1.067146752    vmlinuz                                       303
   1.302104473 = 1.398124032    vmlinuz.old                                   117

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 
```

---

### Post by wilee-nilee on 2012-06-10
You have grub legacy and grub 2 as well they do not work together well.

Use the boot-repair tool to fix this the purge in the advanced is
is what you want.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Or you can do this from the ubuntu install in the terminal

```
sudo apt-get purge grub grub-pc grub-common
```Then
```
sudo apt-get install grub-pc grub-common
```When asked where you want grub choose sda, and tick it with the space bar.

So you can fix the fstab problem as well from the ubuntu install.

The script shows an extra not needed stanza remove this, after opening fstab with.

```
sudo gedit /etc/fstab
```/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

The fstab in the script as far as the swap goes should show the same UUID as when you run this command identifies the swap is as well.

```
sudo blkid
```So when you are done with all of this run this just to make sure your grub is updated.

```
sudo update-grub
```

---

### Post by wrknight on 2012-06-10
Ran Boot-Repair, no change.  I notice that I have Grub legacy in the boot sector of sda, and Grub2 in the "boot sector" of sda1.  sda is the only hard drive on the system.  sda1 is the ext3 filesystem and sda2 is the swap file.  I believe I should purge one of these, but the question I have is whether I should have Grub on the MBR for the hard drive (sda) or on sda1.  My inclination is to put it on sda and purge Grub2 from sda1.  I'm not sure how to purge it from sda1.

---

### Post by wilee-nilee on 2012-06-10
**In the or section **I gave you the exact commands to be run from the Ubuntu desktop. OR means use the tool or run these commands. Notice the word purge in the command.

Since you have run the boot-repair you need to post the script again, as it is after the repair.

If you don't understand the commands or instructions ask for help.

If the tool had been run correctly you would be fixed as far as purging grub legacy and grub 2, and reinstalling grub 2.

You only have one partition to worry about here sda1, the sda2 is the swap, no purge is required there, just the correct stanzas removed from the fstab and the correct UUID's put in or checked to be correct.

There is another set of commands using a chroot from a live cd as well, so post the latest script, and tell us exactly how you want to fix this, from the desktop itself or from a live cd.

---

### Post by wrknight on 2012-06-10
I executed the commands exactly as you wrote them.  (I even copied and pasted them into the command line.)  Here are the results.  As you can see, it updated grub to grub2 in the MBR, but there is still grub legacy installed in the boot sector of sda1.

 
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v) is installed in the boot sector of 
                       sda1 and looks at sector 1181615 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   480,423,824   480,423,762  83 Linux
/dev/sda2         480,423,825   488,392,064     7,968,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        589f4805-7b81-497a-acaa-694b4b85f93e   ext3       
/dev/sda2                                               swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.34-020634-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.34-020634-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.34-020634-generic ...'
	linux	/boot/vmlinuz-2.6.34-020634-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.34-020634-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.28-11-generic ...'
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.27-7-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.27-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.27-7-generic ...'
	linux	/boot/vmlinuz-2.6.27-7-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.27-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.24-16-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.24-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.24-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.24-16-generic ...'
	linux	/boot/vmlinuz-2.6.24-16-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.24-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-2.6.22-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.22-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 589f4805-7b81-497a-acaa-694b4b85f93e
	echo	'Loading Linux 2.6.22-14-generic ...'
	linux	/boot/vmlinuz-2.6.22-14-generic root=UUID=589f4805-7b81-497a-acaa-694b4b85f93e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.22-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=589f4805-7b81-497a-acaa-694b4b85f93e /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda2
UUID=50287a93-4a31-4587-8e98-e155dc5bd544 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  83.660556316 = 89.829838336   boot/grub/core.img                             1
  83.660571575 = 89.829854720   boot/grub/grub.cfg                             1
   3.742286205 = 4.018249216    boot/initrd.img-2.6.22-14-generic              3
   3.759742260 = 4.036992512    boot/initrd.img-2.6.22-14-generic.bak          3
   3.771960735 = 4.050112000    boot/initrd.img-2.6.24-16-generic              3
   3.749534130 = 4.026031616    boot/initrd.img-2.6.24-16-generic.bak          3
   0.856063366 = 0.919191040    boot/initrd.img-2.6.27-7-generic              121
   3.916934490 = 4.205776384    boot/initrd.img-2.6.28-11-generic             122
   1.581634045 = 1.698266624    boot/initrd.img-2.6.31-14-generic             55
   1.616641521 = 1.735855616    boot/initrd.img-2.6.32-21-generic             121
   1.223445415 = 1.313664512    boot/initrd.img-2.6.34-020634-generic         112
   1.373759747 = 1.475063296    boot/initrd.img-2.6.38-8-generic              111
   1.364890575 = 1.465540096    boot/initrd.img-3.0.0-12-generic              176
   1.589992046 = 1.707240960    boot/initrd.img-3.2.0-23-generic              327
   3.761474133 = 4.038852096    boot/vmlinuz-2.6.22-14-generic                 2
   3.763236523 = 4.040744448    boot/vmlinuz-2.6.24-16-generic                 2
   0.658469677 = 0.707026432    boot/vmlinuz-2.6.27-7-generic                  2
   0.748462200 = 0.803655168    boot/vmlinuz-2.6.28-11-generic                 2
   0.525809765 = 0.564583936    boot/vmlinuz-2.6.31-14-generic                22
   0.950587749 = 1.020685824    boot/vmlinuz-2.6.32-21-generic                56
   1.745540142 = 1.874259456    boot/vmlinuz-2.6.34-020634-generic             4
   0.563910961 = 0.605494784    boot/vmlinuz-2.6.38-8-generic                 136
   1.302104473 = 1.398124032    boot/vmlinuz-3.0.0-12-generic                 117
   0.993857861 = 1.067146752    boot/vmlinuz-3.2.0-23-generic                 303
   1.589992046 = 1.707240960    initrd.img                                    327
   1.364890575 = 1.465540096    initrd.img.old                                176
   0.993857861 = 1.067146752    vmlinuz                                       303
   1.302104473 = 1.398124032    vmlinuz.old                                   117

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


```

---

### Post by wrknight on 2012-06-10
I noticed when I executed ```
sudo apt-get purge grub grub-pc grub-common
``` that it tells me it purged everything to do with grub-pc and grub-common, but says there is no grub and doesn't purge grub.  Also there is no reference to Grub Legacy (v) which is listed in the boot sector of sda1.

---

### Post by wilee-nilee on 2012-06-10
> **wrknight said:**
> I executed the commands exactly as you wrote  them.  (I even copied and pasted them into the command line.)  Here are  the results.  As you can see, it updated grub to grub2 in the MBR, but  **there is still grub legacy installed in the boot sector of sda1**.

I'm not sure that, that is important the correct files are in the  actual boot. I have had grub show up in a extended where it would just not be possible. The script can misread some things if a few more apps may need to be installed to get it to read right, with the apps an error may still happen though.

When you ran the purge you would have been asked if you want to completely remove all grub your correct answer would have been yes. You could run them again if you did not say yes with remove all of grub. You can also look in the grub folder and see if grub legacy is actually still there.

I  notice that you have not modified fstab you have an extra stanza not used.

Open a terminal and run this command.

```
sudo blkid
```Now open another terminal and run.

```
sudo gedit /etc/fstab
```Now remove this from the fsatb.
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Now make sure the UUID of sda1 in fstab is the same as the one in the blkid command and the swap UUID is the same as the blkid.

Save the fstab and close it.

Open another terminal and run this to get grub updated.
```
sudo update-grub
```Having a mixture of grub legacy and a incorrect fstab some what work together for the boot problem, but both have to be fixed for everything to work correctly.

So the swap is not actually showing a UUID as well was it part of a encrypted set up?

Is this a encrypted install?

You also have 10 kernel sets you only need two sets.

---

### Post by wilee-nilee on 2012-06-11
> **wrknight said:**
> I noticed when I executed ```
sudo apt-get purge grub grub-pc grub-common
``` that it tells me it purged everything to do with grub-pc and grub-common, but says there is no grub and doesn't purge grub.  Also there is no reference to Grub Legacy (v) which is listed in the boot sector of sda1.

The only area that really matters here are the actual grub files, that I have highlighted, and I tried to explain common errors in the last post. The boot sector type and boot sector info is an error I think, especially if you have run the purge command again and grub was not found.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
   Boot sector info:  Grub Legacy (v) is installed in the boot sector of 
                       sda1 and looks at sector 1181615 of the same hard 
                       drive for the stage2 file, but no stage2 files can be 
                       found at this location.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:       ** /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img**

Part of the problem here is you have not finished all the tasks, nor have you described once this is done how the set up is running.

So lets finish the whole thing and see what is up.

Did you do a grub legacy to grub 2 upgrade sometime in the past with this set up, a command has to be run to get rid of the original grub legacy and accept grub 2 if that is not done I have seen this grub legacy mentioned like this in the past. It does not happen often as it has been awhile since the grub 2 upgrade and so I rarely see it.

---

### Post by wilee-nilee on 2012-06-11
So I have notified another really strong helper in this area to assist, they may not post till tomorrow though, so try to keep the thread updated with what is up if you can. :)

We want you up and running that is the final goal for us here.

---

### Post by oldfred on 2012-06-11
The purge and reinstall will not clear the grub legacy from the PBR - partition boot sector of sda1. But when you boot from MBR with grub2, what is in PBR does not matter and is not used.

My 6 year old  dual core laptop with only 1.5GB of RAM boots in about a minute. But we have had users with BIOS set to use floppy drive when no floppy existed and one who had a CD in and it was doing fsck on the CD??? Is BIOS configured correctly and no extra CDs or Flash drives plugged in?

You do need to get grub2 cleanly installed to the MBR and do some housecleaning of kerneals and the fstab as  wilee-nilee suggested. After reinstalling grub2 and housecleaning rerun boot script and post back.

---

### Post by wrknight on 2012-06-11
Let me try to address all your questions.  
First, I went ahead and deleted the /dev/scd0 entry in fstab, so that is done.

Second, I don't recall upgrading to grub2 except after upgrading to 12.04 and running apt-get install grub grub-pc grub-common and running update-grub. 

Third, the UUID in fstab coincides with the UUID given by blkid.

Fourth, I upgraded to 12.04 from 11.04 by first upgrading to 11.10 using the update manager which automatically did the upgrade.  I did not use an install disc and I don't have one.  (I could make one, but I didn't think I would need it.)

Fifth, apt-get purge grub grub-pc grub-common doesn't appear to even recognize Grub Legacy as the command gives the following message.  ```
Package grub is not installed, so it will not be removed.  The following packages will be removed: grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common*.
```  I agree that the presence of Grub Legacy in the boot sector of sda1 is a problem, but I can't seem to get rid of it.

---

### Post by wilee-nilee on 2012-06-11
Take a look at oldfreds post this is your best help. ;)

---

### Post by wrknight on 2012-06-11
Oh, oh!  I did something very bad.  I tried to use the boot repair program and now what I get on boot is simply "grub"   and beep beep beep beep beep beep. (Obviously my MBR is totally hosed at this time.)

I will make an install disc and try to repair the MBR from that.  Unfortunately, I have to go to class tonight and tomorrow I will be an election officer all day, so I won't be able to get back to this thread until Wednesday.  

Many thanks for your patience.  I'll let you know what happens on Wednesday after I attempt to fix the MBR with an install disc.

Wayne

---

### Post by wrknight on 2012-06-13
I'm back.  Tried to repair MBR from newly created install disc but couldn't find any boot repair utilities on it.  Downloaded boot-repair-disc iso file and burned to disc.  Ran boot repair utility with "recommended" option only.  This restored my MBR and the system is now running as it did before.  After running bootinfoscript the report shows that grub2 is installed in the MBR (sda) and Grub Legacy is installed in the boot sector of sda1.  On boot, the system continues to wait for the disc drive to "get ready" and the "full network" which never shows up.

My other system is a dual boot Windows 7 and ubuntu 11.04.  bootinfoscript reports grub2 installed in the MBR of /dev/sda/ but no other boot info or boot sector in any of the partitions.  

I guess my next questions are

1. Why is there a boot sector in the linux partition?
2. Do we need it?
3. If we don't need it, how do we get rid of it?

Maybe if we got rid of the boot sector in the linux partition, Grub Legacy would go away with it!?     (I'm grasping at straws, here.)

Thanks again for your help.

---

### Post by wrknight on 2012-06-13
Here's more info.  In order to test out the BIOS, I uninstalled the hard drive and replaced it with another hard drive running ubuntu 11.04.  

Total boot time (from power on button) = 40 seconds.

Ran bootinfoscript and the report shows grub2 in the MBR (sda) and nothing in the boot sector of the linux partition (/dev/sda1)

Here's the report from RESULTS.txt is ```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   618,344,447   618,342,400  83 Linux
/dev/sda2         618,346,494   625,141,759     6,795,266   5 Extended
/dev/sda5         618,346,496   625,141,759     6,795,264  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a42ab613-e11e-4f09-9542-1ee469e51251   ext4       
/dev/sda5        6f740da6-76c8-4d39-942d-2ae43f11a35c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=a42ab613-e11e-4f09-9542-1ee469e51251 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=a42ab613-e11e-4f09-9542-1ee469e51251 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a42ab613-e11e-4f09-9542-1ee469e51251 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a42ab613-e11e-4f09-9542-1ee469e51251 ro single 
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
	search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a42ab613-e11e-4f09-9542-1ee469e51251
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a42ab613-e11e-4f09-9542-1ee469e51251 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6f740da6-76c8-4d39-942d-2ae43f11a35c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  40.135513306 = 43.095179264   boot/grub/core.img                             1
  92.176059723 = 98.973290496   boot/grub/grub.cfg                             1
 103.380439758 = 111.003901952  boot/initrd.img-2.6.38-11-generic              2
  92.329101562 = 99.137617920   boot/initrd.img-2.6.38-8-generic               2
 102.763008118 = 110.340939776  boot/vmlinuz-2.6.38-11-generic                 1
  40.133792877 = 43.093331968   boot/vmlinuz-2.6.38-8-generic                  1
 103.380439758 = 111.003901952  initrd.img                                     2
  92.329101562 = 99.137617920   initrd.img.old                                 2
 102.763008118 = 110.340939776  vmlinuz                                        1
  40.133792877 = 43.093331968   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  98 a4 be f1 f2 1d ac ec  91 ec 23 aa f8 0a 3b c1  |..........#...;.|
00000010  bd cf 1b 2a 0e 61 42 51  cf 4e bb 1e cd 57 e0 f5  |...*.aBQ.N...W..|
00000020  37 d7 af fa 8d e2 81 22  d4 c5 7f 62 90 cc 88 3e  |7......"...b...>|
00000030  27 78 a9 bb 44 62 92 45  82 9a 67 24 c2 6d 91 d5  |'x..Db.E..g$.m..|
00000040  34 42 15 8b 57 48 92 c8  eb 9f ea df 5c 9a f7 a3  |4B..WH......\...|
00000050  90 fa ce 9d 8e 22 e6 dd  c9 58 df ac 2e 7a 78 ca  |....."...X...zx.|
00000060  7c 0b 0b 6d 2a af f4 8d  b4 72 ff 31 fd 13 1d c9  ||..m*....r.1....|
00000070  0a f5 26 64 15 b5 7f ee  8b 60 a4 33 7b e8 09 9c  |..&d.....`.3{...|
00000080  e7 33 0d 39 ca 88 e3 aa  48 07 4e 18 c7 2d 3c df  |.3.9....H.N..-<.|
00000090  fa 5e c2 df 65 78 8a 52  46 f0 1e d2 db 31 5f 0c  |.^..ex.RF....1_.|
000000a0  e3 4f 12 98 ee a0 f0 ef  73 6f 99 f9 97 92 e0 25  |.O......so.....%|
000000b0  91 db 6f f9 21 31 ca 18  c3 fc c1 cf e4 ea 21 8e  |..o.!1........!.|
000000c0  6f 3b 78 2d dc 65 7d 37  f9 7e 81 f3 e3 d7 d5 1a  |o;x-.e}7.~......|
000000d0  ce 69 ac bf 8a f1 b8 dc  37 8e 47 9f cc f9 b0 3f  |.i......7.G....?|
000000e0  5f e0 71 1f de 3f fc 8e  73 28 79 a4 bc e3 f1 9e  |_.q..?..s(y.....|
000000f0  33 73 9f e8 7b 79 5f 39  67 f0 e9 72 09 5d bd 46  |3s..{y_9g..r.].F|
00000100  47 bf 19 e2 3b bd e7 60  fd 3d 9b 76 52 e2 01 9e  |G...;..`.=.vR...|
00000110  ec 04 f9 97 fb 5c 7e 5f  9b b3 8d fc 48 17 d8 f1  |.....\~_....H...|
00000120  93 12 50 f2 76 01 e4 bf  bd 7c 6d 30 7e 45 7e 46  |..P.v....|m0~E~F|
00000130  5e e9 93 06 f4 1e 84 1f  42 4d 22 a1 c8 15 f2 1f  |^.......BM".....|
00000140  39 64 c7 da 0e ee 23 b4  be fe 67 a4 26 f0 ff fe  |9d....#...g.&...|
00000150  59 a2 48 df 0f 58 7f ff  0d f1 47 85 7d fe 87 44  |Y.H..X....G.}..D|
00000160  c1 44 53 d9 57 38 61 af  60 86 e2 58 35 d7 92 c4  |.DS.W8a.`..X5...|
00000170  6c 92 54 62 82 b1 66 a7  24 3e e8 91 38 e8 ac db  |l.Tb..f.$>..8...|
00000180  d3 1b f3 21 dc aa af 8c  c4 49 b8 c3 c1 96 58 e2  |...!.....I....X.|
00000190  95 d9 35 5d 09 15 79 64  91 3a c6 0d fe 64 fc cc  |..5]..yd.:...d..|
000001a0  60 9b f4 9a f2 9a 8a b1  ce 53 8d 15 c6 12 d7 1b  |`........S......|
000001b0  d2 3a d5 d0 57 11 2a 70  3e 9f 25 a8 50 74 00 fe  |.:..W.*p>.%.Pt..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 67 00 00 00  |............g...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


``` 

So the system boots up in 40 seconds from a hard drive running ubuntu 11.04, but still takes up to 5 minutes to boot up from the hard drive that I upgraded to 12.04

---

### Post by oldfred on 2012-06-13
Since this is a different drive it is hard to make comparisons. But I would make a copy of dmesg from Log File Viewer or /var/log and compare with the one from 12.04. It will not be exact because of the changes but may highlight where all the extra time is going.

---

### Post by wrknight on 2012-06-13
Here's the output from dmesg where the main delay occurs.```
[   33.535585] ADDRCONF(NETDEV_UP): tap0: link is not ready
[   43.200050] eth0: no IPv6 routers present
[  153.348121] type=1400 audit(1339637948.110:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1279 comm="apparmor_parser"
[  153.349084] type=1400 audit(1339637948.110:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1278 comm="apparmor_parser"
[  153.351472] type=1400 audit(1339637948.110:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1280 comm="apparmor_parser"
[  153.351931] type=1400 audit(1339637948.110:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1280 comm="apparmor_parser"
[  153.354680] type=1400 audit(1339637948.114:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1280 comm="apparmor_parser"
[  153.360576] type=1400 audit(1339637948.122:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1283 comm="apparmor_parser"
[  153.361263] type=1400 audit(1339637948.122:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1283 comm="apparmor_parser"
[  153.362620] type=1400 audit(1339637948.122:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1281 comm="apparmor_parser"
[  153.365970] type=1400 audit(1339637948.126:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1284 comm="apparmor_parser"
[  153.366513] type=1400 audit(1339637948.126:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1284 comm="apparmor_parser"
[  153.631086] init: kdm main process (1358) killed by TERM signal
[  153.636545] init: gdm main process (1389) killed by TERM signal
[  157.773537] postgres (1788): /proc/1788/oom_adj is deprecated, please use /proc/1788/oom_score_adj instead.

``` After 157.77 everything goes smoothly and there are no more messages after 161.60.  

There is also a short delay due to the hard drive not being ready.  This occurs at 6.60.
Messages are as follows:

[    6.595136] EXT3-fs (sda1): recovery required on readonly filesystem
[    6.595140] EXT3-fs (sda1): write access will be enabled during recovery
[    9.845879] kjournald starting.  Commit interval 5 seconds
[    9.845999] EXT3-fs (sda1): recovery complete
[    9.846489] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   32.306756] ADDRCONF(NETDEV_UP): eth0: link is not ready

On the 11.04 hard drive, there are no messages about file system recovery. The file system is mounted at 1.38 and the message about ipv6 routers not being present occurs at 21.34. That's the end of the messages.  (Boot up is completed at that time.)

---

### Post by oldfred on 2012-06-13
I know nothing about apparmor.
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Is sda1 running fsck on every boot? You may want to run e2fsck on sda1.

Must be unmounted:
Try "e2fsck -f /dev/sda1". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.


#From liveCD so everything is unmounted,swap off if necessary, change example shown with sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by wrknight on 2012-06-14
Not sure I understand what to do.  (I'm still a newbie at this so please be patient.)

If I understand you correctly, the first thing I need is a live CD.  This is something I don't have, so it's going to take a little doing to get to that point.

Once I have the live CD, I boot to it and then run 
sudo e2fsck -C0 -p -f -v /dev/sda1 
to check the drive for errors and if it reports errors then I run 
sudo e2fsck -f -y -v /dev/sda1
to fix the errors. 

Do I have that right?

---

### Post by wrknight on 2012-06-14
Having squandered a lot of time without getting anywhere, I have to ask a really dumb question.  What is liveCD, where do I get one and if I can't get one, how do I make one?

---

### Post by fbicknel on 2012-06-14
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

I suggest you use a USB flash drive if you have a 1GB USB drive laying around.  Much faster to create and to boot, not to mention you can overwrite it when a new version comes along.

Google ubuntu create a live usb

---

### Post by wrknight on 2012-06-15
Back again.  Used liveCD to run e2fsck. No errors or bad blocks found.  Ran e2fsck -f -y -v anyway and no problems were found and nothing was fixed.  Rebooted from hard drive with same 5 minute boot up delays.

So far, everything I have tried has failed.  I still have the gut feeling that the Grub Legacy in the boot sector of sda1 is causing problems and I'm still trying to find out how to get rid of that.  Any suggestions on that will be appreciated.

---

