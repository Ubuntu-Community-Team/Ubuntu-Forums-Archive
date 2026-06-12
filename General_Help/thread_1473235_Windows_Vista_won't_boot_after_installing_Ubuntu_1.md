---
title: "Windows Vista won't boot after installing Ubuntu 10.04"
date: 2010-05-05
forum: General Help
---

### Post by Curse on 2010-05-05
I got this laptop today and decided to dual boot Linux, as I've been using it for a bit on an older laptop. 
I downloaded and installed Ubunutu 10.04, using the first install option to have it install next to Windows, and afterwards on startup I get 6 options:

[img]http://i170.photobucket.com/albums/u279/Andrelommech/DSC_0001.jpg[/img]

Whenever I try to boot with either of the Windows options, it goes to the Windows loading bar, then the screen goes black and the computer resets.

Help? :/ I was a total idiot and didn't make recovery disks. I already had Vista recovery disks and I did try that, but it said I wouldn't be able to restore the system with them. F11 on startup splashscreen does nothing.

Oh, and please keep in mind I'm a bit of a layman :mad:

---

### Post by wilee-nilee on 2010-05-05
So does the Vista recovery have a auto repair or are you running commands via the MS terminal?

Post this script to see whats going on. Paste the read out script to the thread highlight it then click on # in the post in thread gui.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/newreply.php
[HTML]http://newyork.ubuntuforums.org/showthread.php?t=1437155[/HTML]

---

### Post by Curse on 2010-05-05
> **nitstorm said:**
> ubuntuforums.orgubuntuforums.org/newreply.php
[HTML]http://newyork.ubuntuforums.org/showthread.php?t=1437155[/HTML]

I did the "How to" at the bottom of the first post [here](http://ubuntuforums.org/showthread.php?t=1014708), for Vista, and upon reboot all I get is a flashing _ in the top left after the splash screen

---

### Post by wilee-nilee on 2010-05-05
> **Curse said:**
> I did the "How to" at the bottom of the first post [here](http://ubuntuforums.org/showthread.php?t=1014708), for Vista, and upon reboot all I get is a flashing _ in the top left after the splash screen

first I would post the boot script. But here is a link to Microsoft instructions use at your own risk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Here is another thread post #4 has the commands and instructions you need I think this is compatible with vista and W7.
[http://ubuntuforums.org/showthread.php?t=1466021](http://ubuntuforums.org/showthread.php?t=1466021)
I think this thread will fix it but without knowing more it is difficult to tell whats going on. If you let the install resize vista the thread has a chkdsk command maybe it will clean that up.
The thread link is basically a condensed version of the MS link so having both for reference may help, good luck.

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> first I would post the boot script. But here is a link to Microsoft instructions use at your own risk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Here is another thread post #4 has the commands and instructions you need I think this is compatible with vista and W7.
[http://ubuntuforums.org/showthread.php?t=1466021](http://ubuntuforums.org/showthread.php?t=1466021)
I think this thread will fix it but without knowing more it is difficult to tell whats going on. If you let the install resize vista the thread has a chkdsk command maybe it will clean that up.
The thread link is basically a condensed version of the MS link so having both for reference may help, good luck.

Tried what was outlined in post 4. No dice. Same flashing _

---

### Post by wilee-nilee on 2010-05-05
So post the boot script and tell us did you use the live cd to resize the Vista partition? As you are maybe starting to realize is that quick fixes are not working. Also since it is a new computer how are you getting to the command line to run the commands, you need to tell us more if you really want help.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This script is how things get done around here most of the time, it gets to the heart of the matter, which would be helpful along with your information on resizing the Vista partition. This will be my last post if you just don't post the script.

---

### Post by rnerwein on 2010-05-05
> **Curse said:**
> I got this laptop today and decided to dual boot Linux, as I've been using it for a bit on an older laptop. 
I downloaded and installed Ubunutu 10.04, using the first install option to have it install next to Windows, and afterwards on startup I get 6 options:

[GRUB version 1.97]
Linux
Linux recovery
memtest
memtest (something else here)
Windows Vista /dev/sda1
Windows Vista /dev/sda2

Those last two options may not be 100%, I can reboot and update if needed.

Whenever I try to boot with either of the Windows options, it goes to the Windows loading bar, then the screen goes black and the computer resets.

Help? :/ I was a total idiot and didn't make recovery disks. I already had Vista recovery disks and I did try that, but it said I wouldn't be able to restore the system with them. F11 on startup splashscreen does nothing.

Oh, and please keep in mind I'm a bit of a layman :mad:

hi
i got exacly the same.
then i try to boot from Windows Vista /dev/sda2  ( normaly the recovery ) and this works well.
Vista ain't  start the recovery mode ---> it starts normal. 
have a look at my fdisk output about /dev/sda1 :mad:

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
[COLOR=Red]/dev/sda1               1        1828    14680064   27  Unbekannt[/COLOR]
/dev/sda2   *        1828       46484   358701056    7  HPFS/NTFS
/dev/sda3           46484       58566    97046524    7  HPFS/NTFS
/dev/sda4           58567       91201   262140607    f  W95 Erw. (LBA)
/dev/sda5           58567       58828     2104483+  82  Linux Swap / Solaris
/dev/sda6           58829       61439    20972826   83  Linux
/dev/sda7           61440       70425    72180013+  83  Linux
/dev/sda8           70426       82663    98301703+  83  Linux
/dev/sda9           82664       91201    68581453+  83  Linux

may be the same as yours - have a look with: sudo fdisk -l /dev/sda
else what you can see - the boot flag is on /dev/sda2 not on the Unkonwn /dev/sda1 !

ciao

---

### Post by wilee-nilee on 2010-05-05
> **rnerwein said:**
> hi
i got exacly the same.
then i try to boot from Windows Vista /dev/sda2  ( normaly the recovery ) and this works well.
Vista ain't  start the recovery mode ---> it starts normal. 
have a look at my fdisk output about /dev/sda1 :mad:

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
[COLOR=Red]/dev/sda1               1        1828    14680064   27  Unbekannt[/COLOR]
/dev/sda2   *        1828       46484   358701056    7  HPFS/NTFS
/dev/sda3           46484       58566    97046524    7  HPFS/NTFS
/dev/sda4           58567       91201   262140607    f  W95 Erw. (LBA)
/dev/sda5           58567       58828     2104483+  82  Linux Swap / Solaris
/dev/sda6           58829       61439    20972826   83  Linux
/dev/sda7           61440       70425    72180013+  83  Linux
/dev/sda8           70426       82663    98301703+  83  Linux
/dev/sda9           82664       91201    68581453+  83  Linux

may be the same as yours - have a look with: sudo fdisk -l /dev/sda
else what you can see - the boot flag is on /dev/sda2 not on the Unkonwn /dev/sda1 !

ciao

Do not hijack another's thread, your problems may seem similar but they are not the same

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> So post the boot script and tell us did you use the live cd to resize the Vista partition? As you are maybe starting to realize is that quick fixes are not working. Also since it is a new computer how are you getting to the command line to run the commands, you need to tell us more if you really want help.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This script is how things get done around here most of the time, it gets to the heart of the matter, which would be helpful along with your information on resizing the Vista partition. This will be my last post if you just don't post the script.

I've been running them through the Windows startup disk I made by downloading from a link in the 'How to' thread. 

I'm starting up the computer now with the Ubuntu disk to run the script. I would have done it earlier but I'm not familiar with it :x Thanks for your patience!

---

### Post by Curse on 2010-05-05
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   128,754,923   128,754,861   7 HPFS/NTFS
/dev/sda2    *    213,768,192   234,434,559    20,666,368   c W95 FAT32 (LBA)
/dev/sda3         128,755,710   213,768,191    85,012,482   5 Extended
/dev/sda5         128,755,712   210,190,335    81,434,624  83 Linux
/dev/sda6         210,192,384   213,768,191     3,575,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3E307AD638979553                       ntfs                                     
/dev/sda2        F8640F9F640F602C                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        08f7306e-e127-4056-bb0a-7ed3e9612b3d   ext4                                     
/dev/sda6        e753f148-7c61-4a38-98bd-61e695554098   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
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
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3e307ad638979553
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f8640f9f640f602c
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
UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e753f148-7c61-4a38-98bd-61e695554098 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  70.3GB: boot/grub/core.img
  87.5GB: boot/grub/grub.cfg
  70.4GB: boot/initrd.img-2.6.32-21-generic
  70.3GB: boot/vmlinuz-2.6.32-21-generic
  70.4GB: initrd.img
  70.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by wilee-nilee on 2010-05-05
Put this in code tags for easy reading, hold on.
```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Windows is installed in the MBR of /dev/sda

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Vista: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /bootmgr

sda3: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 63 128,754,923 128,754,861 7 HPFS/NTFS
/dev/sda2 * 213,768,192 234,434,559 20,666,368 c W95 FAT32 (LBA)
/dev/sda3 128,755,710 213,768,191 85,012,482 5 Extended
/dev/sda5 128,755,712 210,190,335 81,434,624 83 Linux
/dev/sda6 210,192,384 213,768,191 3,575,808 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 3E307AD638979553 ntfs
/dev/sda2 F8640F9F640F602C ntfs HP_RECOVERY
/dev/sda3: PTTYPE="dos"
/dev/sda5 08f7306e-e127-4056-bb0a-7ed3e9612b3d ext4
/dev/sda6 e753f148-7c61-4a38-98bd-61e695554098 swap
/dev/sda: PTTYPE="dos"
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)


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
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
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
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 3e307ad638979553
chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f8640f9f640f602c
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=e753f148-7c61-4a38-98bd-61e695554098 none swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


70.3GB: boot/grub/core.img
87.5GB: boot/grub/grub.cfg
70.4GB: boot/initrd.img-2.6.32-21-generic
70.3GB: boot/vmlinuz-2.6.32-21-generic
70.4GB: initrd.img
70.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

```

---

### Post by wilee-nilee on 2010-05-05
I'm not sure where to go, but the reason I was so insistent on this script, is that there are others on the forum who are very good at this. So let us know if you used the Ubuntu install to resize vista at the Ubuntu install. I think your in good shape it just takes the right person to help. You also might post the laptop model.

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> I'm not sure where to go, but the reason I was so insistent on this script, is that there are others on the forum who are very good at this. So let us know if you used the Ubuntu install to resize vista at the Ubuntu install. I think your in good shape it just takes the right person to help. You also might post the laptop model.

Its an HP G50, 32bit, 2gb DDR2

I used the first install option, I believe it was autoresize the windows install?

Either way, your help is greatly appreciated. You're not getting paid to be on here, and I definitely understand your request to use the script.

---

### Post by wilee-nilee on 2010-05-05
> **Curse said:**
> Its an HP G50, 32bit, 2gb DDR2

I used the first install option, I believe it was autoresize the windows install?

Either way, your help is greatly appreciated. You're not getting paid to be on here, and I definitely understand your request to use the script.

I have seen people have problems with a usb device plugged in, is the sdb a wireless thumb or a printer or something if so unplug it and try to see if the boot works.

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> I have seen people have problems with a usb device plugged in, is the sdb a wireless thumb or a printer or something if so unplug it and try to see if the boot works.

I've got nothing plugged into the computer

---

### Post by nitstorm on 2010-05-05
ubuntuforums.orgubuntuforums.org/showthread.php
> 
/dev/sda2    *    213,768,192   234,434,559    20,666,368   c W95 FAT32 (LBA)
/dev/sda2        F8640F9F640F602C                       ntfs       HP_RECOVERY                   
ubuntuforums.orgubuntuforums.org/newreply.php


Maybe its got something to do with the fact that the bootloader is from the recovery section and not sda1 which has the Vista mbr, but I have no clue. I just found this out of the normal and pointed out. Better wait till the Linux & Ubuntu heroes and masters of the Grub arrive..

---

### Post by wilee-nilee on 2010-05-05
> **nitstorm said:**
> ubuntuforums.orgubuntuforums.org/showthread.php
ubuntuforums.orgubuntuforums.org/newreply.php


Maybe its got something to do with the fact that the bootloader is from the recovery section and not sda1 which has the Vista mbr, but I have no clue. I just found this out of the normal and pointed out. Better wait till the Linux & Ubuntu heroes and masters of the Grub arrive..

You may correct on that, so @Cursor if you boot the live cd you can use gparted to change the boot to sda1 without any damage and if that isn't the answer then you can set the boot back to sda2. To set the boot on a partition you right click on the partition in gparted, you want to change then manage flags then tick boot in the list. I think if you just change sda1 it automatically removes it from sda2.

I wonder also if you boot with the computer off, if you start hitting the f8 key immediately after hitting the power button if it would go to the safe boot options. 

Try one or the other options but I would avoid changing the boot and trying the f8 prompt at a first boot attempt. That is what I would do anyway.

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> You may correct on that, so @Cursor if you boot the live cd you can use gparted to change the boot to sda1 without any damage and if that isn't the answer then you can set the boot back to sda2. To set the boot on a partition you right click on the partition in gparted, you want to change then manage flags then tick boot in the list. I think if you just change sda1 it automatically removes it from sda2.

I wonder also if you boot with the computer off, if you start hitting the f8 key immediately after hitting the power button if it would go to the safe boot options. 

Try one or the other options but I would avoid changing the boot and trying the f8 prompt at a first boot attempt. That is what I would do anyway.

That makes a lot of sense. I've gotten the Linux boot to work again by following the first on the 'How to' link. I think its wanting to use the recovery partition to boot from when I tell it to boot to Windows at the GRUB menu......... will be back shortly with results! (changing the boot flag, that is)

---

### Post by Curse on 2010-05-05
Alright. Tried changing the flag to no avail. I only tried booting from Windows on /dev/sd1. F8 did nothing on startup after restarting, maybe it's F2? 

Here's a 'screenshot' of my current boot menu. [Link](http://i170.photobucket.com/albums/u279/Andrelommech/DSC_0001.jpg)

---

### Post by wilee-nilee on 2010-05-05
> **Curse said:**
> Alright. Tried changing the flag to no avail. I only tried booting from Windows on /dev/sd1. F8 did nothing on startup after restarting, maybe it's F2? 

Here's a 'screenshot' of my current boot menu. [Link](http://i170.photobucket.com/albums/u279/Andrelommech/DSC_0001.jpg)

Boot Ubuntu and run ```
sudo update-grub
```

Then try the sda1 at grub choice at boot.

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> Boot Ubuntu and run ```
sudo update-grub
```

Then try the sda1 at grub choice at boot.

Just tried, went to Microsoft scroll bar and then restarted like it's been doing :mad:

---

### Post by wilee-nilee on 2010-05-05
So I am lost again, what we want to do for sure is to make sure if anybody helps you that the bootscript is up to date with however you have the boot set. This time of night there are usually people on who know this stuff. 

The good thing is that it is a brand new computer so I am pretty sure if you need to reinstall Vista, that you can get a DVD or ISO to burn from HP. It just has to be the install that will auto activate. 

Thanks to the other post I had wondered about the boot partition, so at the least we tried that.

I suspect this can be fixed it needs more experienced hands at work. It sounds like you have Ubuntu back so that is good.

So if you need to post another boot script, paste it to the thread then highlight the whole script then click on the # symbol in that same window that will make it the scrolling text.

---

### Post by Curse on 2010-05-05
Updated boot_info_script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   128,754,923   128,754,861   7 HPFS/NTFS
/dev/sda2         213,768,192   234,434,559    20,666,368   c W95 FAT32 (LBA)
/dev/sda3         128,755,710   213,768,191    85,012,482   5 Extended
/dev/sda5         128,755,712   210,190,335    81,434,624  83 Linux
/dev/sda6         210,192,384   213,768,191     3,575,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3E307AD638979553                       ntfs                                     
/dev/sda2        F8640F9F640F602C                       ntfs       HP_RECOVERY                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        08f7306e-e127-4056-bb0a-7ed3e9612b3d   ext4                                     
/dev/sda6        e753f148-7c61-4a38-98bd-61e695554098   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
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
search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 08f7306e-e127-4056-bb0a-7ed3e9612b3d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3e307ad638979553
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f8640f9f640f602c
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
UUID=08f7306e-e127-4056-bb0a-7ed3e9612b3d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e753f148-7c61-4a38-98bd-61e695554098 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  70.3GB: boot/grub/core.img
  75.1GB: boot/grub/grub.cfg
  70.4GB: boot/initrd.img-2.6.32-21-generic
  70.3GB: boot/vmlinuz-2.6.32-21-generic
  70.4GB: initrd.img
  70.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by wilee-nilee on 2010-05-05
bump

---

### Post by Curse on 2010-05-05
Perhaps I need to re-download and install GRUB? Could there have been a bug in what I installed?

---

### Post by Curse on 2010-05-05
Perhaps the answer lies in the first paragraph [here](http://ubuntuforums.org/showthread.php?t=1195275), and the [link](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210) contained? 

Not sure how I'd add a file to the C: drive from Linux though...

---

### Post by wilee-nilee on 2010-05-05
> **Curse said:**
> Perhaps the answer lies in the first paragraph [here](http://ubuntuforums.org/showthread.php?t=1195275), and the [link](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210) contained? 

Not sure how I'd add a file to the C: drive from Linux though...

I bumped because I noticed that some were on line that are the ones needed. I would be careful about continuing to mess with the MBR while people may be trying to help, I noticed yesterday that this seemed to be going on. Do what you want but, if you do stuff extra while being helped not part of the instructions it is like a rat chasing it's tail in order to fix this.

---

### Post by ebro173 on 2010-05-05
I can't give the source because I don't remember where I saw it.  But, I think I read that the safest way to install Ubuntu these days (on a machine where you want to keep the existing Windows install and dual boot) is to resize the Windows partition from within Windows.  Doing it this way would create some amount of unallocated space at the end of the hard disk.  I specifically think that what I read went on to say that if you don't do it this way (if you let the Ubuntu install process resize the partitions) then you won't be able to boot windows after installing Ubuntu.

I did resize the windows partition from within windows and then used the Ubuntu installer to set up my Ubuntu install.  I can successfully dual boot.  

What was frustrating about using the windows utility to resize the windows partition was that I couldn't really resize the windows partition as small as I wanted to.  So I've got a massive ~100GB Windows partition and I will use that very rarely.

Anyway, sorry I can't give you suggestions on how to fix your problem but maybe this will help you on the path to determine what went wrong so you can fix it.

Edit: sorry, just read over everything here.  Looks like help should already be on the way.  And my point was already covered.

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> I bumped because I noticed that some were on line that are the ones needed. I would be careful about continuing to mess with the MBR while people may be trying to help, I noticed yesterday that this seemed to be going on. Do what you want but, if you do stuff extra while being helped not part of the instructions it is like a rat chasing it's tail in order to fix this.

Indeed, that is a good point. I feel like a child in a forest when it comes to this stuff...

---

### Post by wilee-nilee on 2010-05-05
> **Curse said:**
> Indeed, that is a good point. I feel like a child in a forest when it comes to this stuff...

Don't worry, you have Ubuntu working and a brand new computer under warranty. I would call HP and see about getting a DVD from them for a backup and a fixing tool, while waiting.

We all get anxious, to get things done, and a brand new computer would make me the same way were only human.

For the other post you are talking about resizing W7, although with vista a person should resize it after a full defragging several times with a live CD using gparted, then reboot to make sure it is working then install the second operating system.

---

### Post by oldfred on 2010-05-05
You posted links to a wubi problem. Wubi is a version installed inside the windows partition and does not apply to you.

Your boot script looks normal except for the comment on sda2 posted above, but that should not prevent sda1 from booting as it has all the files. Was the install on sda1 a install over XP. Vista and 7 now start at 2048. New installs of 7 have an additional 100MB boot partitions, but the files normally in that are in your sda1. XP and linux start at 63 (may be different with lucid). If the partition was moved from 2048 to 63 windows needs the full set of repairs ( or more correctly I do not know which actually fixes it).

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd


You may want to run the fixMBR so you can directly boot windows to know it works, then you can reinstall grub2 and run the sudo update-grub to make sure it sees the windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by wilee-nilee on 2010-05-05
> **ebro173 said:**
> I can't give the source because I don't remember where I saw it.  But, I think I read that the safest way to install Ubuntu these days (on a machine where you want to keep the existing Windows install and dual boot) is to resize the Windows partition from within Windows.  Doing it this way would create some amount of unallocated space at the end of the hard disk.  I specifically think that what I read went on to say that if you don't do it this way (if you let the Ubuntu install process resize the partitions) then you won't be able to boot windows after installing Ubuntu.

I did resize the windows partition from within windows and then used the Ubuntu installer to set up my Ubuntu install.  I can successfully dual boot.  

What was frustrating about using the windows utility to resize the windows partition was that I couldn't really resize the windows partition as small as I wanted to.  So I've got a massive ~100GB Windows partition and I will use that very rarely.

Anyway, sorry I can't give you suggestions on how to fix your problem but maybe this will help you on the path to determine what went wrong so you can fix it.

Edit: sorry, just read over everything here.  Looks like help should already be on the way.  And my point was already covered.

As far as resizing you need a optimizing defragger that will move everything to the front of the partition that can be like.
[http://www.auslogics.com/en/software/disk-defrag/download/](http://www.auslogics.com/en/software/disk-defrag/download/)
there are even better ones but this one works great just look at the preferences.

---

### Post by Curse on 2010-05-05
> **oldfred said:**
> 
Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd


You may want to run the fixMBR so you can directly boot windows to know it works, then you can reinstall grub2 and run the sudo update-grub to make sure it sees the windows.


When I've done that, I just get a flashing _ in the top left after the BIOS splash screen :(

To be 100% clear, the laptop is about a year old model, but was only recently opened. It is Windows Vista Home Preimium.

---

### Post by wilee-nilee on 2010-05-05
> **Curse said:**
> When I've done that, I just get a flashing _ in the top left after the BIOS splash screen :(

To be 100% clear, the laptop is about a year old model, but was only recently opened. It is Windows Vista Home Preimium.

Just so you know this is the person you want help from amongst others, also remember that it seemed that part of the problem was being very careful to run the commands correctly and, to stick with instructions. Yes this didn't work last time but the boot was on sdfa2 at that time, no cause and effect. Follow his instructions if you feel brave today.

---

### Post by Curse on 2010-05-05
> **wilee-nilee said:**
> Just so you know this is the person you want help from amongst others, also remember that it seemed that part of the problem was being very careful to run the commands correctly and, to stick with instructions. Yes this didn't work last time but the boot was on sdfa2 at that time, no cause and effect. Follow his instructions if you feel brave today.

Copy that, rebooting with the Windows disk :)

---

### Post by Curse on 2010-05-05
As I should have known, y'all were right. It worked this time! 

Now I have to see about getting GRUB back on there and working so I can boot to Linux..

---

### Post by wilee-nilee on 2010-05-05
> **Curse said:**
> As I should have known, y'all were right. It worked this time! 

Now I have to see about getting GRUB back on there and working so I can boot to Linux..

Hang on this is what you do follow step 11.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)
Yipee is what I say. ;)

---

### Post by nitstorm on 2010-05-05
Been following your thread for a while and pretty happy that you found the solution :) Cheers mate and sorry I couldn't be of much use :) Put back the Grub and let us know :)

---

### Post by wilee-nilee on 2010-05-05
> **nitstorm said:**
> Been following your thread for a while and pretty happy that you found the solution :) Cheers mate and sorry I couldn't be of much use :) Put back the Grub and let us know :)

Actually you were helpful as I believe the boot was on the wrong partition. ;) Well at least we will know soon anyway, the sda2 boot probably was okay to begin with, my XP oem had the boot running from the recovery.

---

### Post by oldfred on 2010-05-05
Glad you got it working.

wilee-nilee is probably correct that you were booting thru the recovery. Windows usually combines multiple installs into one partition for booting and then lets you choose. Perhaps it could not see to fix sda1 without the flag moved to that partition. You may then not be able to get to the recovery partition but I do not have a high opinion of recovery partitions, I would just install Ubuntu.

---

### Post by bwsmith7 on 2010-05-05
> **oldfred said:**
> You posted links to a wubi problem. Wubi is a version installed inside the windows partition and does not apply to you.

Your boot script looks normal except for the comment on sda2 posted above, but that should not prevent sda1 from booting as it has all the files. Was the install on sda1 a install over XP. Vista and 7 now start at 2048. New installs of 7 have an additional 100MB boot partitions, but the files normally in that are in your sda1. XP and linux start at 63 (may be different with lucid). If the partition was moved from 2048 to 63 windows needs the full set of repairs ( or more correctly I do not know which actually fixes it).

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr #updates MBR master boot record do not run if you still want grub
chkdsk /r
BootRec.exe /FixBoot #updates PBR partition boot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd


You may want to run the fixMBR so you can directly boot windows to know it works, then you can reinstall grub2 and run the sudo update-grub to make sure it sees the windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Thank you oldfred! I can get back into Windows now! I am a complete newbie, but your instructions were clear and easy to follow. I don't know how to get back into Linux, but once someone comes up with an easy and dependable way to dual-boot again without messing up my Windows 7, I will do it. Thanks again!

---

### Post by Curse on 2010-05-06
Hey guys, thanks again for all the help!! I've been really busy the last couple days but I think later tonight I'll try to get GRUB back on there, and trust me, if it doesn't work, y'all will be the first to know! :p

---

### Post by wilee-nilee on 2010-05-07
> **Curse said:**
> Hey guys, thanks again for all the help!! I've been really busy the last couple days but I think later tonight I'll try to get GRUB back on there, and trust me, if it doesn't work, y'all will be the first to know! :p

If this gives you any solace, the motherboard, or Ethernet port on my 9 month old acer netbook has gone south, or at least I have lost the Ethernet, still have wireless. So I did everything including a reinstall of W7 with Lucid still on the same HD, and just reinstalled grub and I am typing this from Lucid. No Ethernet on W7 or Lucid, this is a hardware problem. So it is easy to get grub reloaded. I will be sending it to repair tomorrow.

Big thanks goes to oldfred on this one, I wanted to suggest the same thing he did, but I just thought, let the people who do this regularly get it correct

---

### Post by amarendra on 2010-05-07
Can't boot into Vista after upgrade to 10.04 (using alternate CD). However Fedora is fine. All three (**Vista, Fedora, Ubuntu**) are/were installed on separate partitions. "**System>Administration>Disk Utility**" shows my Vista partition is not **bootable** (is this the reason?).

Boot Info Script result:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 109517401 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 109555777 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Fedora release 12 (Constantine) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 109614913 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 109614977 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 109615041 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda7 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    73,422,847    73,420,800   7 HPFS/NTFS
/dev/sda2    *     73,422,848   104,902,655    31,479,808  83 Linux
/dev/sda4         104,904,511   312,578,047   207,673,537   f W95 Ext d (LBA)
/dev/sda5         167,823,360   230,756,351    62,932,992   7 HPFS/NTFS
/dev/sda6         230,758,400   293,691,391    62,932,992   b W95 FAT32
/dev/sda7         293,693,440   312,578,047    18,884,608   b W95 FAT32
/dev/sda8         104,904,513   165,132,134    60,227,622  83 Linux
/dev/sda9         165,132,198   167,814,989     2,682,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D436D96036D943E0                       ntfs                                     
/dev/sda2        dc63f387-57e3-450d-8a75-98f85c67c995   ext4       Fedora-12-i686-L              
/dev/sda4: PTTYPE="dos" 
/dev/sda5        681AFDCE1AFD98F0                       ntfs       Geek's Paradise               
/dev/sda6        BA81-EE93                              vfat       MEDIA                         
/dev/sda7        806E-CF8C                              vfat       STOCK                         
/dev/sda8        b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7   ext4                                     
/dev/sda9        263b8dcd-7517-4230-bd9d-6ae68ccff794   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


=============================== sda2/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Wed Jan 20 04:37:17 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=dc63f387-57e3-450d-8a75-98f85c67c995 /                       ext4    defaults        1 1
UUID=263b8dcd-7517-4230-bd9d-6ae68ccff794 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda2: Location of files loaded by Grub: ===================


  39.6GB: boot/initramfs-2.6.31.5-127.fc12.i686.img
  40.9GB: boot/initramfs-2.6.31.9-174.fc12.i686.img
  39.2GB: boot/vmlinuz-2.6.31.5-127.fc12.i686
  39.5GB: boot/vmlinuz-2.6.31.9-174.fc12.i686

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro  splash vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 ro single  splash vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d436d96036d943e0
	chainloader +1
}
menuentry "Fedora release 12 (Constantine) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set dc63f387-57e3-450d-8a75-98f85c67c995
	linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 root=/dev/sda2
}
menuentry "Fedora release 12 (Constantine) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set dc63f387-57e3-450d-8a75-98f85c67c995
	linux /boot/vmlinuz-2.6.31.9-174.fc12.i686 root=/dev/sda2
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=b44d4a7c-96a5-4c51-9b1a-0a62b0c186b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=263b8dcd-7517-4230-bd9d-6ae68ccff794 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


  56.0GB: boot/grub/core.img
  54.0GB: boot/grub/grub.cfg
  84.3GB: boot/initrd.img-2.6.31-19-generic
  83.7GB: boot/initrd.img-2.6.31-20-generic
  84.3GB: boot/initrd.img-2.6.31-21-generic
  83.8GB: boot/initrd.img-2.6.32-21-generic
  67.4GB: boot/vmlinuz-2.6.31-19-generic
  70.9GB: boot/vmlinuz-2.6.31-20-generic
  72.5GB: boot/vmlinuz-2.6.31-21-generic
  64.5GB: boot/vmlinuz-2.6.32-21-generic
  83.8GB: initrd.img
  84.3GB: initrd.img.old
  64.5GB: vmlinuz
  72.5GB: vmlinuz.old

```

---

### Post by oldfred on 2010-05-07
amarendra, You should start your own thread, but your problem is very common. IF this does not solve it start a new thread.
See my comment in this thread.
[http://ubuntuforums.org/showthread.php?t=1471896&highlight=Vista](http://ubuntuforums.org/showthread.php?t=1471896&highlight=Vista)

This is your problem as this is the windows partition and the  boot sector has to have window in it.
Grub 2 is installed in the boot sector of sda1

This solves it for most. Some also have to run windows repairs or other fixes.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by amarendra on 2010-05-07
Won't making the Windows partition ( sda1 ) bootable solve the problem? I tried it using Disk Utility but didn't succeed.

---

### Post by amarendra on 2010-05-07
My problem solved.
Replied here [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9256036](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9256036)

---

### Post by Curse on 2010-05-11
Followed this: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Vista is boots fine, Ubuntu boots fine.

Marking this thread as solved, thank you so much!

---

