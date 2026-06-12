---
title: "I've suffered a catastrophe!"
date: 2010-08-24
forum: General Help
---

### Post by Quackers on 2010-08-24
Oh dear :-( I uninstalled Evolution and everything associated with it and my system won't boot any more - even with 2 x Ubuntu and a Mac OS X system to choose from.
I tried sudo apt-get update && sudo apt-get install ubuntu-desktop   but all that hapened was about 100 "failed to fetch" entries whizzed by.
Ok, I thought I have a seperate Home partition I'll just re-install. 4 installs later I can't even get to grub. It's just saying error: no such device abc6xxxx-duwy-xxxx-xxxx-xxxxxxxxx
blah blah.
If I boot into live cd I can see my 64 bit system sitting there but I can't boot it.
I'm thinking trashing my /dev/sdb by reformatting with GParted and starting again. But on the other hand it seems harsh to lose 3 OSes because I deleted an email program.

Any suggestions would be welcome. Thanks.

---

### Post by d3v1150m471c on 2010-08-24
recover your data with a live cd, try reinstalling and/or repairing your grub menu.

---

### Post by Quackers on 2010-08-24
There really doesn't seem to be any point re-installing any more. I think all I need is to install grub to /dev/sdb but I can't manage it. It won't run - or I'm doing something wrong.

---

### Post by oleink on 2010-08-24
> **Quackers said:**
> There really doesn't seem to be any point re-installing any more. I think all I need is to install grub to /dev/sdb but I can't manage it. It won't run - or I'm doing something wrong.

You chose to FULLY remove Evolution?  If so does anyone know what languages it is coded in??

---

### Post by Quackers on 2010-08-24
It did work! In 32 bit and 64 bit, that isn't the issue. 
In my experience OS X has far less hardware supported than Ubuntu.
Anyway, I've tried to re-install grub from the live cd, but no go.I've tried update-grub but that says @cannot find a device for /

---

### Post by oleink on 2010-08-24
> **Quackers said:**
> It did work! In 32 bit and 64 bit, that isn't the issue. 
In my experience OS X has far less hardware supported than Ubuntu.
Anyway, I've tried to re-install grub from the live cd, but no go.I've tried update-grub but that says @cannot find a device for /

So wait you have grub now?

---

### Post by Quackers on 2010-08-24
I'm afraid not

---

### Post by Rubi1200 on 2010-08-24
Hi Quackers,
sorry to hear about your problems.

First the lecture: never try and remove default programs; they are all so intertwined you can really mess things up. If you don't want something, just don't use it and hide it in the menu.

If you fully removed Evolution, you took out, oops, dbus!!! amongst other things.

Ok, lecture over.

So, if you are on the LiveCD, please post the results of the bootscript linked to at the bottom of my post.

Let's start from there.

---

### Post by oleink on 2010-08-24
> **Quackers said:**
> I'm afraid not

So what exactly do you have?  Are you in an xterm session automatically or have you not gotten quite that far yet either?

---

### Post by WorMzy on 2010-08-24
Bit late now, but don't uninstall evolution; ubuntu considers it an integral part of ubuntu-desktop, so if you uninstall it, you install pretty much everything related to gnome.

Can you boot a liveCD and run the [boot info script]("http://sourceforge.net/projects/bootinfoscript/")?

You won't need to wipe the drive, so don't worry about that. We just need to fix grub.

Unfortunately, I have no experience with grub 2, so it may take a while unless someone else can direct you, or there's a decent tutorial out there (there probably is).

---

### Post by Quackers on 2010-08-24
Hokey cokey, here we go

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046     5,859,327     5,857,282   5 Extended
/dev/sda5               2,048     5,859,327     5,857,280  82 Linux swap / Solaris
/dev/sda2    *      5,859,328    39,258,111    33,398,784  83 Linux
/dev/sda3         293,844,915   488,392,064   194,547,150  af HFS
/dev/sda4          39,258,112   293,842,943   254,584,832  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046     5,859,327     5,857,282   5 Extended
/dev/sdb5               2,048     5,859,327     5,857,280  82 Linux swap / Solaris
/dev/sdb2    *      5,859,328    30,273,535    24,414,208  83 Linux
/dev/sdb3          30,273,536   188,477,439   158,203,904  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        fcd9dfad-cafb-45aa-a2ef-c604a194808a   ext4                                     
/dev/sda3        1a6aa2b2-6cb5-3c59-a3c7-79e612695c87   hfsplus    Snow Leopard                  
/dev/sda4        25e2ec92-c462-4ef8-a538-36116ac8787c   ext4                                     
/dev/sda5        a65962f1-18e9-4aeb-934e-fa2ecdeaad65   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        a0f9ca15-a968-4dd6-9cc8-087d4650f462   ext4                                     
/dev/sdb3        e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2   ext4                                     
/dev/sdb5        add3dc6e-bcd4-4f6b-8282-280a16d2636f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set fcd9dfad-cafb-45aa-a2ef-c604a194808a
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set fcd9dfad-cafb-45aa-a2ef-c604a194808a
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set fcd9dfad-cafb-45aa-a2ef-c604a194808a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fcd9dfad-cafb-45aa-a2ef-c604a194808a ro   quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda3)" {
	insmod hfsplus
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4c38836e478ad4e1
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 4c38836e478ad4e1 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=fcd9dfad-cafb-45aa-a2ef-c604a194808a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=25e2ec92-c462-4ef8-a538-36116ac8787c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a65962f1-18e9-4aeb-934e-fa2ecdeaad65 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=0615874e-e425-412e-81b5-4a1467f615cc none            swap    sw              0       0



=================== sda2: Location of files loaded by Grub: ===================


  16.0GB: boot/grub/core.img
   5.3GB: boot/grub/grub.cfg
  16.6GB: boot/initrd.img-2.6.32-24-generic
  16.5GB: boot/vmlinuz-2.6.32-24-generic
  16.6GB: initrd.img
  16.5GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a0f9ca15-a968-4dd6-9cc8-087d4650f462 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=a0f9ca15-a968-4dd6-9cc8-087d4650f462 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set a0f9ca15-a968-4dd6-9cc8-087d4650f462
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set fcd9dfad-cafb-45aa-a2ef-c604a194808a
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=fcd9dfad-cafb-45aa-a2ef-c604a194808a ro quiet splash nomodeset video=uvesafb:mode_option=1920x1200-24,mtrr=3,scroll=ywrap
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Mac OS X (32-bit) (on /dev/sda3)" {
	insmod hfsplus
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4c38836e478ad4e1
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 4c38836e478ad4e1 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda3)" {
	insmod hfsplus
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 4c38836e478ad4e1
        insmod vbe
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 4c38836e478ad4e1 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=a0f9ca15-a968-4dd6-9cc8-087d4650f462 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a65962f1-18e9-4aeb-934e-fa2ecdeaad65 none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
  12.0GB: boot/grub/grub.cfg
   3.6GB: boot/initrd.img-2.6.32-24-generic
   3.4GB: boot/vmlinuz-2.6.32-24-generic
   3.6GB: initrd.img
   3.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  01 00 34 22 20 76 61 6c  75 65 3d 22 42 41 51 41  |..4" value="BAQA|
00000010  41 41 3d 3d 22 2f 3e 0a  20 20 20 20 20 20 20 20  |AA=="/>.        |
00000020  3c 53 65 74 4b 65 79 56  61 6c 75 65 20 70 61 74  |<SetKeyValue pat|
00000030  68 3d 22 5c 52 65 67 69  73 74 72 79 5c 4d 41 43  |h="\Registry\MAC|
00000040  48 49 4e 45 5c 53 4f 46  54 57 41 52 45 5c 4d 69  |HINE\SOFTWARE\Mi|
00000050  63 72 6f 73 6f 66 74 5c  46 75 73 69 6f 6e 5c 47  |crosoft\Fusion\G|
00000060  41 43 43 68 61 6e 67 65  4e 6f 74 69 66 69 63 61  |ACChangeNotifica|
00000070  74 69 6f 6e 5c 44 65 66  61 75 6c 74 22 20 6e 61  |tion\Default" na|
00000080  6d 65 3d 22 53 74 6f 72  65 43 68 61 6e 67 65 49  |me="StoreChangeI|
00000090  44 46 6f 72 33 32 42 69  74 50 72 6f 63 65 73 73  |DFor32BitProcess|
000000a0  65 73 22 20 74 79 70 65  3d 22 30 78 30 30 30 30  |es" type="0x0000|
000000b0  30 30 30 34 22 20 65 6e  63 6f 64 69 6e 67 3d 22  |0004" encoding="|
000000c0  62 61 73 65 36 34 22 20  76 61 6c 75 65 3d 22 42  |base64" value="B|
000000d0  41 51 41 41 41 3d 3d 22  2f 3e 0a 20 20 20 20 20  |AQAAA=="/>.     |
000000e0  20 20 20 3c 53 65 74 4b  65 79 56 61 6c 75 65 20  |   <SetKeyValue |
000000f0  70 61 74 68 3d 22 5c 52  65 67 69 73 74 72 79 5c  |path="\Registry\|
00000100  4d 41 43 48 49 4e 45 5c  53 4f 46 54 57 41 52 45  |MACHINE\SOFTWARE|
00000110  5c 4d 69 63 72 6f 73 6f  66 74 5c 46 75 73 69 6f  |\Microsoft\Fusio|
00000120  6e 5c 47 41 43 43 68 61  6e 67 65 4e 6f 74 69 66  |n\GACChangeNotif|
00000130  69 63 61 74 69 6f 6e 5c  44 65 66 61 75 6c 74 22  |ication\Default"|
00000140  20 6e 61 6d 65 3d 22 50  72 65 73 65 6e 74 61 74  | name="Presentat|
00000150  69 6f 6e 46 72 61 6d 65  77 6f 72 6b 2c 33 2e 30  |ionFramework,3.0|
00000160  2e 30 2e 30 2c 2c 33 31  62 66 33 38 35 36 61 64  |.0.0,,31bf3856ad|
00000170  33 36 34 65 33 35 2c 6d  73 69 6c 22 20 74 79 70  |364e35,msil" typ|
00000180  65 3d 22 30 78 30 30 30  30 30 30 30 33 22 20 65  |e="0x00000003" e|
00000190  6e 63 6f 64 69 6e 67 3d  22 62 61 73 65 36 34 22  |ncoding="base64"|
000001a0  20 76 61 6c 75 65 3d 22  4f 41 50 31 4e 72 72 55  | value="OAP1NrrU|
000001b0  79 67 45 3d 22 2f 3e 0a  20 20 20 20 20 20 00 20  |ygE="/>.      . |
000001c0  21 00 82 b9 4d 6c 02 00  00 00 00 60 59 00 00 00  |!...Ml.....`Y...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda3

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb ff 02 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200


```

I'm sure it won't be pretty

---

### Post by Quackers on 2010-08-24
Just by way of explanation I'm now booted into the live cd.
I definitely won't be removing anything major again :-) What a dork!
I'd just downloaded Thunderbird and got it running, so I thought it would be a good idea to get rid of Evolution. Not so, it seems :-)
Thanks for the help peoples

---

### Post by WorMzy on 2010-08-24
Interesting, you have two grubs. I assume it's loading the one on sda; but both seem to be fine. I mean, as far as I can tell. All UUIDs check out in any case.

I did notice that the fstab on sda2 has two swap partitions listed, and one of them is using a non-existent UUID. I doubt this is preventing you from booting, but removing it won't do any harm. So mount that partition and use "gksu gedit" to remove these lines from it's /etc/fstab file

```
# swap was on /dev/sdb2 during installation
UUID=0615874e-e425-412e-81b5-4a1467f615cc none            swap    sw              0       0
```

There may be a problem if grub is being loaded from sdb, as all the menu items in that grub.cfg file set the root to hd1,X, and unless it works differently in grub 2, grub always counts the disk that it's on as hd_0_, not hd1 (or higher). So you may want to use gedit's find and replace dialogue box to change all mentions of hd1 to hd0 in that file, just in case that's what's causing the problem.

---

### Post by Quackers on 2010-08-24
It seems that the swap partition on /dev/sdb is being picked up in the fstab for /dev/sda (as /dev/sdb2). Oh dear what have I done?

---

### Post by Quackers on 2010-08-24
What does the first line of this mean - the /dev/loop0 bit?

```
ubuntu@ubuntu:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="fcd9dfad-cafb-45aa-a2ef-c604a194808a" TYPE="ext4" 
/dev/sda3: UUID="1a6aa2b2-6cb5-3c59-a3c7-79e612695c87" LABEL="Snow Leopard" TYPE="hfsplus" 
/dev/sda4: UUID="25e2ec92-c462-4ef8-a538-36116ac8787c" TYPE="ext4" 
/dev/sda5: UUID="a65962f1-18e9-4aeb-934e-fa2ecdeaad65" TYPE="swap" 
/dev/sdb2: UUID="a0f9ca15-a968-4dd6-9cc8-087d4650f462" TYPE="ext4" 
/dev/sdb3: UUID="e4d4bb4e-7d8f-4400-ad94-8d89ef5898e2" TYPE="ext4" 
/dev/sdb5: UUID="add3dc6e-bcd4-4f6b-8282-280a16d2636f" TYPE="swap" 
```

---

### Post by Rubi1200 on 2010-08-24
Not certain, but pretty sure it refers to the CD drive and LiveCD because squashfs is read-only.

---

### Post by Quackers on 2010-08-24
What would you think about deleting grub from sdb (if I can do that) and see if it boots? Does that seem reasonable?

---

### Post by Rubi1200 on 2010-08-24
> **Quackers said:**
> What would you think about deleting grub from sdb (if I can do that) and see if it boots? Does that seem reasonable?
According to the bootscript, GRUB is looking at sda5 (swap) even though the files are on sda2.


Why not first try and reinstall GRUB on sda and then see what happens?
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Worst comes to the worst, we think of another solution.

---

### Post by Quackers on 2010-08-24
Rubi, Rubi, Rubi :-) The first method in your link has got me back into the 32 bit install (on sda) and the grub menu lists the OS X installation too :-)
I'm going to run sudo update-grub now and see if it picks up the 64 bit install as well.
Very, very niiiiiiiice :-)

---

### Post by Rubi1200 on 2010-08-24
Excellent!!!

Let me know what happens please.

:D

---

### Post by Quackers on 2010-08-24
update-grub found the 64 bit version too! I'm going to push my luck and try and boot into it :-) I'll be in touch......or not :-)

---

### Post by WorMzy on 2010-08-24
Good eye, Rubi, I completely missed that. :O

---

### Post by Chris1274 on 2010-08-24
I did that a few weeks ago and wrecked my system, necessitating a total re-install. I marked Evolution for complete removal, and then realized things were not going to end well when it started removing Python. The end result was a more-or-less illiterate OS.

---

### Post by Quackers on 2010-08-24
Yes, Chris, I too was thoroughly sickened.
WorMzy, I missed it too, and I was looking specifically for something like that! Maybe some new glasses for me!
Rubi, the reboot went well :-) I'm back into 64 bit now. Unfortunately somewhere along the line my previous Home partition got overwritten, but all in all it's not a bad result in the circumstances.
Many thanks to all participators and particularly to Rubi's eagle-eye! 
I can go to bed now - I think 20 hours messing about is enough!

---

### Post by Rubi1200 on 2010-08-24
> **Quackers said:**
> Yes, Chris, I too was thoroughly sickened.
WorMzy, I missed it too, and I was looking specifically for something like that! Maybe some new glasses for me!
Rubi, the reboot went well :-) I'm back into 64 bit now. Unfortunately somewhere along the line my previous Home partition got overwritten, but all in all it's not a bad result in the circumstances.
Many thanks to all participators and particularly to Rubi's eagle-eye! 
I can go to bed now - I think 20 hours messing about is enough!
Good! Glad it worked out :D

And let this be a lesson to all; do **not** try and remove Evolution!

Sleep well, you deserve it!

---

### Post by Quackers on 2010-08-24
zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz
What, what? Oh yes - don't remove Evolution! Definitely not!  :-)

---

### Post by Rubi1200 on 2010-08-24
Can you mark the thread Solved please. Will help others who run into similar difficulties.

---

### Post by alphaamanitin on 2010-08-24
> **Rubi1200 said:**
> Good! Glad it worked out :D

And let this be a lesson to all; do **not** try and remove Evolution!

Sleep well, you deserve it!


This is crap.  If I wanted a system that made it nearly impossible for me to remove default programs I would stick with Macs and Windows computers.  This is a serious bug that needs to be fixed.  

AlphaA

---

### Post by Quackers on 2010-08-24
Happy and relieved to do that :-)

---

### Post by keithpeter on 2010-08-24
Hello Quackers and all

Glad you got your grub back without a wipe and re-install.

My personal solution to not liking Evolution and some of the other defaults, but quite liking Ubuntu itself on my desktop was to install Ubuntu Studio 10.04. At a certain point in the install, you are asked which of four bundles that you want. 

I just *unticked all four of them*, and got a clean Ubuntu with just Firefox and some basic apps like VLC, Braseo, Sound Recorder and the Gnome apps.

Then I updated and added what *I* wanted. :twisted:

Ubuntu Studio has its own issues of course, I had some work to do to get the Nvidia drivers working properly.

On my T42 laptop, I built up a minimal Gnome-core based system - again, then you can install what you want to. That was a bit more fiddling though.

---

### Post by Quackers on 2010-08-24
Thanks for the suggestion keithpeter. The only thing is, as soon as I get a decision to make things tend to go downhill :-)
After all the trials and tribulations of the last 20 odd hours there is good news! My webcam is now recognised, and works lol.

---

### Post by Irony on 2010-08-24
You can uninstall the email side of evolution without a problem, 'cos I have and everything is fine.

---

### Post by Quackers on 2010-08-24
Irony, it's not that I don't believe you, it's just that my fingers are still burning! And my eyes :-) But thanks for the info.

---

### Post by Rubi1200 on 2010-08-24
> **Irony said:**
> You can uninstall the email side of evolution without a problem, 'cos I have and everything is fine.
Care to share how you did it?

---

### Post by WorMzy on 2010-08-24
Well, technically only evolution-data-server is required, since gnome-control-center, empathy, and gnome-panel depend on it. If you could keep that somehow, then you could remove the rest.

---

### Post by Quackers on 2010-08-24
I deleted everything with Evolution in the name and all dependencies, child processes or whatever they are. I was obviously a bit heavy-handed.

---

### Post by Irony on 2010-08-24
> **Rubi1200 said:**
> Care to share how you did it?
I went to synaptic and uninstalled it - this is in 10.04 64 bit. I use thunderbird.

I've uninstalled it in previous versions as well. In fact in the past I've also uninstalled the other bits of evolution - the only ill effect being that I couldn't change my password in the gui (so I did it from terminal). Probably best not to uninstall evolution-data-server-common.

---

### Post by Chris1274 on 2010-08-24
> **alphaamanitin said:**
> This is crap.  If I wanted a system that made it nearly impossible for me to remove default programs I would stick with Macs and Windows computers.  This is a serious bug that needs to be fixed.  

AlphaA

It can be removed, you just have to be careful not to remove the dependencies along with it. Using Synaptic Package Manager, mark it just for "removal" and not for "complete removal".

---

