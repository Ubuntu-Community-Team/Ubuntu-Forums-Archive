---
title: "Windows XP not selectable?"
date: 2010-11-29
forum: General Help
---

### Post by LuniTux on 2010-11-29
Hello,

I recently installed lubuntu 10.10 on my Toshiba nb205. Everything works out of the box but the sound is really quiet even at max volume. This is not my main concern though. I also have Windows XP installed on the same computer. The problem is, after I installed lubuntu 10.10, Windows XP no longer shows up as a selectable os when I turn on the netbook. I can access the windows XP partition correctly through lubuntu and everything seems ok, but I need to be able to boot from windows xp (unfortunately). Is there a way to redetect my OSes on the computer?

Thanks,

---

### Post by Rubi1200 on 2010-11-29
It is possible that GRUB is not picking up the XP install for some reason.

First, run ```
sudo update-grub
``` from within Ubuntu.

If that does not help, run the boot info script linked at the bottom of my post and get the results back here for us to take a look.

Thanks.

---

### Post by LuniTux on 2010-11-30
sorry about the response delay. I will try that as soon as I get home.

---

### Post by Rubi1200 on 2010-11-30
No problem, let us know if you need any other help.

---

### Post by LuniTux on 2010-12-04
when I run ```
sudo update-grub
```
I get```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```
my computer does not seem to recognize that I have windows xp installed. is there a way to manually add it?

---

### Post by oldfred on 2010-12-04
To see your exact configuration as Rubi1200 already suggested:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by LuniTux on 2010-12-05
sorry, I completly missed the part about running boot script. Here are the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

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

/dev/sda1    *             63    97,656,312    97,656,250   7 HPFS/NTFS
/dev/sda2          97,656,830   312,580,095   214,923,266   5 Extended
/dev/sda5          97,656,832   304,766,975   207,110,144  83 Linux
/dev/sda6         304,769,024   312,580,095     7,811,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        EAEC270BEC26D21D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f442021d-7133-49a1-b469-787b7826443b   ext4                                     
/dev/sda6        52b286af-2627-4f20-80e5-3b1a27dd5fef   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

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
search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=f442021d-7133-49a1-b469-787b7826443b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=f442021d-7133-49a1-b469-787b7826443b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f442021d-7133-49a1-b469-787b7826443b ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=f442021d-7133-49a1-b469-787b7826443b ro single 
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
	search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set f442021d-7133-49a1-b469-787b7826443b
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
UUID=f442021d-7133-49a1-b469-787b7826443b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=52b286af-2627-4f20-80e5-3b1a27dd5fef none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 114.5GB: boot/grub/core.img
 114.6GB: boot/grub/grub.cfg
  50.7GB: boot/initrd.img-2.6.35-22-generic
  51.2GB: boot/initrd.img-2.6.35-23-generic
 114.5GB: boot/vmlinuz-2.6.35-22-generic
 114.5GB: boot/vmlinuz-2.6.35-23-generic
  51.2GB: initrd.img
  50.7GB: initrd.img.old
 114.5GB: vmlinuz
 114.5GB: vmlinuz.old

```

---

### Post by cavalier911 on 2010-12-05
Boot files from WinXP look good. Grub 2 os-prober script is failing to see WinXP located at /dev/sda1,in grub2 speak is (hd0,1)
```
gksudo gedit /etc/grub.d/40_custom
```
Copy/Paste below existing comments:
```
menuentry "WinXP" {
set root=(hd0,1)
insmod chain
chainloader +1 
}
```
Save
```
sudo update-grub
```
This should add the WinXP menu entry to /boot/grub/grub.cfg 
When chosen from bootmenu will chainload WinXP's bootloader

---

### Post by LuniTux on 2010-12-05
THANK YOU!!!!

that worked perfectly. Are there any updates or anything that I should avoid that could re-disable winXP?

---

### Post by bailout on 2010-12-06
You don't have to manually edit grub. For some reason Lubuntu doesn't install the software that detects other OSs 'os-prober'. You just needed to install that package and update grub. See this post

[http://ubuntuforums.org/showthread.php?p=10031199](http://ubuntuforums.org/showthread.php?p=10031199)

---

### Post by cavalier911 on 2010-12-07
LuniTux
Your welcome,it's ok to upgrade grub2, 40_custom is not overwritten on an update.
The custom entry for WinXP will be added whenever update-grub is run.
If you reconfigure your hardware so the WinXP drive is no longer /dev/sda1 
but for example 
/dev/sdb1 -----> set root=(hd1,1)
/dev/sdc1 -----> set root=(hd2,1)
/dev/sdd1 -----> set root=(hd3,1)

Rerun the bootinfo script , set root for new location of WinXP indicated in boot info summary.

---

### Post by LuniTux on 2010-12-09
Ok, thanks for all the help :)

---

