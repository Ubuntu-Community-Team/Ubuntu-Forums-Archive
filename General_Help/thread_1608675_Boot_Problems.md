---
title: "Boot Problems"
date: 2010-10-29
forum: General Help
---

### Post by ftabor on 2010-10-29
Ever since the installation of 10,04 I have been experiencing boot problems. I thought it was a hd dying and installed a new hard drive and installed 10.04 fresh reusing ~home. The problem continues with 10.10. This may be a BIOS or motherboard issue, but I'll outline the error message I'm getting and see if anyone has any insight.

To start out, when cold booting or restarting I began to get this error. At first, restarting would complete a boot. Then it got to where I would have to run the liveCD then reboot. Now it takes about an hour of rebooting from liveCD before it will eventually start. In the last 2 or three days or so, I've been getting the old style Grub boot menu before it tries to boot.

Here is the error:

```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check Rootdelay= (Did the system wait long enough?)
 -Check Root= (Did the system wait for the right device?)
-Missing Modules (cat /proc/modules:ls /dev)

Alert! /dev//disk/by-uuid/b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa does not exist. Dropping to shell!

Busybox shell (ash)

Type help for list of commands.

(initramfs) _

```

I presume by-uuid/b8b2b111-b4dd-4d39-b6f5-9b200fe8cda is the id of my hd,

This list of commands brings up nothing useful for rebooting, Only repeatedly trying to reboot finally works,

Any help would be appreciated, I'm afraid that the next time I try to restart is going to leave me dead in the water.

---

### Post by drs305 on 2010-10-29
Check what happens when you run these commands. Change "sda1" to your Ubuntu partition. If the results match what follows the # symbol...

```
sudo mount /dev/sda1 /mnt        # Fails
sudo mount -t ext4 /dev/sda1     # Works
blkid /dev/sda1                  # No result 
blkid -p /dev/sda1               # Ambivalent result

```

If these are the results you get, there was a bug that might be cured by the making an empty file (replace extX with filesystem - ext2, ext3, or ext4)  :
```
sudo mount /dev/sda1 /mnt
*or*
sudo mount -t extX /dev/sda1 /mnt
sudo touch /mnt/testfile
```

If this doesn't work, please run the boot info script from the following link and post the contents of the RESULTS.txt.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by ftabor on 2010-10-29
sudo mount /dev/sda1 /mnt 

It mounted.

sudo mount -t ext4 /dev/sda1

Already mounted as /mnt

blkid /dev/sda1

No return

blkid -p /dev/sda1

Permission denied,

I'm going to unmount it from /mnt and try the other three commands.

Can't unmount it from /mnt. From System Monitor /dev/sda shows mounted as / and as /mnt.

---

### Post by ftabor on 2010-10-29
I'm going to get one step ahead and before I make any changes, here are the results from the bootinfo script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    19,531,775    19,529,728  83 Linux
/dev/sda2          19,533,822 1,250,263,039 1,230,729,218   5 Extended
/dev/sda5       1,236,592,640 1,250,263,039    13,670,400  82 Linux swap / Solaris
/dev/sda6          19,533,824 1,236,592,639 1,217,058,816  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        13f1600e-52bd-430c-b32f-ac83120c342c   swap                                     
/dev/sda6        59da4f29-80d8-4425-b1b4-60c99a2b4b1e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b8b2b111-b4dd-4d39-b6f5-9b200fe8cdaa /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=59da4f29-80d8-4425-b1b4-60c99a2b4b1e /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=13f1600e-52bd-430c-b32f-ac83120c342c none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.7GB: boot/grub/core.img
   5.4GB: boot/grub/grub.cfg
   7.1GB: boot/initrd.img-2.6.32-25-generic
    .8GB: boot/initrd.img-2.6.35-22-generic
   3.9GB: boot/vmlinuz-2.6.32-25-generic
   2.9GB: boot/vmlinuz-2.6.35-22-generic
    .8GB: initrd.img
   2.9GB: vmlinuz
```

---

### Post by drs305 on 2010-10-29
Things look ok in the boot info results. The only thing I note is that if you run "sudo fdisk -l" you may get a "partitions not in disk order". It's correctable but really shouldn't affect the booting.

What I normally recommend in cases where Grub might be confused is to purge and reinstall it. It won't fix an MBR or disk problem, but it will fix any corrupted Grub2 files.

If you follow the procedure, just make sure you have an Internet connection before you purge grub.

Here is the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by ftabor on 2010-10-29
I followed the steps:

```
sudo mount /dev/sda1 /mnt
or
sudo mount -t extX /dev/sda1 /mnt
sudo touch /mnt/testfile
```

and got 2 reliable restarts with out the Grub menu appearing. I'll save the link to the Grub purge and see if this continues to work.

Thanks very much for your assistance,

---

