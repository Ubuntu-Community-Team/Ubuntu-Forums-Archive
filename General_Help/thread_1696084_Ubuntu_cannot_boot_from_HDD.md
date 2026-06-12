---
title: "Ubuntu cannot boot from HDD"
date: 2011-02-26
forum: General Help
---

### Post by stephenstop on 2011-02-26
OK.  i have downgraded from Ubuntu 10.10 to Ubuntu 10.04.  I've had some bumps along the way and finally was able to install 10.04 successfully.  Right now, my computer will not boot from the HDD and will only boot from the USB drive that the LiveCD is on.  When I reorganize to set HDD as primary boot, i get:

id-laptop login:
id-laptop password:

and I can put that in but then it just gives me a command line that ends with ~$ i believe.  How do I get it to boot from the HDD instead of from the USB without running into this problem?

If I resequence the boot to HDD as number two, it will juts go into the LiveCD mode.  Am I supposed to reinstall 10.04 again? I know 10.04 was successfully installed because it said it was and it needed to restart so i hit the restart button.  It also had my old desktop picture there and all my files AND i checked the system info before restarting (it confirmed that lucid lynx was running).

PLEASE HELP I am new to ubuntu and do not know much about commands.

---

### Post by wilee-nilee on 2011-02-26
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.
 
Have the thumb plugged in when running the script.

---

### Post by stephenstop on 2011-02-26
```
                                                                     
                                                                     
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    74,840,063    74,838,016  83 Linux
/dev/sda2          74,842,110    78,139,391     3,297,282   5 Extended
/dev/sda5          74,842,112    78,139,391     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1040 MB, 1040711680 bytes
128 heads, 40 sectors/track, 397 cylinders, total 2032640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             40     2,032,639     2,032,600   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        56ce346e-85ea-4313-964c-048307320f76   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f29b9fd7-f5ab-4724-ad2d-44e5875038bc   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1                                               vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=56ce346e-85ea-4313-964c-048307320f76 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56ce346e-85ea-4313-964c-048307320f76
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=56ce346e-85ea-4313-964c-048307320f76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f29b9fd7-f5ab-4724-ad2d-44e5875038bc none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
   6.7GB: boot/grub/grub.cfg
   4.7GB: boot/initrd.img-2.6.32-28-generic
    .9GB: boot/initrd.img-2.6.35-22-generic
   1.1GB: boot/initrd.img-2.6.35-24-generic
   2.8GB: boot/initrd.img-2.6.35-25-generic
   4.6GB: boot/vmlinuz-2.6.32-28-generic
   4.5GB: boot/vmlinuz-2.6.35-22-generic
   4.5GB: boot/vmlinuz-2.6.35-24-generic
   4.6GB: boot/vmlinuz-2.6.35-25-generic
   4.7GB: initrd.img
   4.6GB: vmlinuz
```

---

### Post by wilee-nilee on 2011-02-27
First confirm you still have the media you wanted saved by booting the live cd and look at the install partition.

You can't downgrade from 10.10 to 10.04 it has to be a fresh install, confirm what you did if you can.

If your getting to the login and password then a command line type startx to start the desktop.

---

### Post by stephenstop on 2011-02-27
This is how i downgraded from 10.10 to 10.04

[http://www.youtube.com/watch?v=QGnsYuWS0xY](http://www.youtube.com/watch?v=QGnsYuWS0xY)

---------------------------------------------------------------
When I removed the USB livecd, and it restarted, it just goes to the screen where it says:

id-laptop login:
Password:

Last login
Linux owner-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i 686 GNU/Linux
Uvuntu 1`0.04.2 LTS

Welcome to Ubuntu!
* Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

0 packages can be updated 0 updates are security updates

id@id-laptop:~$

--------------------------------------------------------------

After the first reboot after installation, I had my old settings but it was on Linux 10.04 (I checked the About Ubuntu info to confirm it was 10.04).  Then it downloaded some updates and needed to restart.  So I hit the restart button and now the screen is just what I typed above everytime I turn on the computer.

If I type startx, it says:

_________________________________________________________________
(EE) intel (0): Failed to initialize kernel memory manager
(EE) intel(0): AGP GART support is either not available or cannot be used. Make sure your kernel has agpgart support or has the agpgart module loaded.
(EE) intel (0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0

Please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing log giving up.
xinit: No such file or directory (errno 2): unabl3e to connect to X server
xinit: No such process (errno 3): Server error.
id@id-laptop:~$
_________________________________________________________________

---

