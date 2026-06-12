---
title: "Grub wont boot Windows 7"
date: 2011-01-23
forum: General Help
---

### Post by Enkh-Amgalan on 2011-01-23
I HP pavillion dv2715nr with Windows 7 Professional 32 bit and Ubuntu 10.10 64-bit. I first install Windows 7 then installed Ubuntu 10.10 64 bit (grub2). And upgraded to Kubuntu. I can log on Ubuntu.

Problem: If I select Windows 7 from grub menu screen goes black and nothing happens.

How to fix it.

Thankh you for all your help.

BR,
Eegii

---

### Post by Rubi1200 on 2011-01-23
Hi and welcome to the forums :)

We need to get a better overview of your current setup.

To that end, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Enkh-Amgalan on 2011-01-24
Thank you for your reply.

Shell's result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 290646880 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    79,874,047    79,667,200   7 HPFS/NTFS
/dev/sda3          79,874,048   260,098,047   180,224,000   7 HPFS/NTFS
/dev/sda4         260,100,094   312,580,095    52,480,002   5 Extended
/dev/sda5         260,100,096   264,003,583     3,903,488  82 Linux swap / Solaris
/dev/sda6         264,005,632   312,580,095    48,574,464  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7CB8BF93B8BF4A82                       ntfs       System Reserved               
/dev/sda2        CC7432957432826E                       ntfs                                     
/dev/sda3        C604274F04274233                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        77f6f5cb-3de0-4a05-a6c1-13bc8e5e86fb   swap                                     
/dev/sda6        d2a1751c-790d-4d2e-bad2-e9850cc4b7ba   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d2a1751c-790d-4d2e-bad2-e9850cc4b7ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=d2a1751c-790d-4d2e-bad2-e9850cc4b7ba ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d2a1751c-790d-4d2e-bad2-e9850cc4b7ba ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d2a1751c-790d-4d2e-bad2-e9850cc4b7ba ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set d2a1751c-790d-4d2e-bad2-e9850cc4b7ba
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 7cb8bf93b8bf4a82
	chainloader +1
}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d2a1751c-790d-4d2e-bad2-e9850cc4b7ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=77f6f5cb-3de0-4a05-a6c1-13bc8e5e86fb none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 148.9GB: boot/grub/core.img
 142.0GB: boot/grub/grub.cfg
 136.1GB: boot/initrd.img-2.6.35-22-generic
 136.4GB: boot/initrd.img-2.6.35-24-generic
 148.7GB: boot/vmlinuz-2.6.35-22-generic
 148.7GB: boot/vmlinuz-2.6.35-24-generic
 136.4GB: initrd.img
 136.1GB: initrd.img.old
 148.7GB: vmlinuz
 148.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  00 00 01 ba 45 5c 86 60  04 01 01 89 c3 f8 00 00  |....E\.`........|
00000010  01 e0 07 ec 81 00 00 47  3b 43 c6 93 b9 1e 1a 12  |.......G;C......|
```

---

### Post by Quackers on 2011-01-24
In sda1 you will see the last line looks like this
```
/bootmgr /Boot/BCD /grldr
```
The entry for /grldr should not be there. 
These will be in the root of your C: drive in Windows. The /grldr folder may be inside a folder called /boot. If you see that folder, open it up and if grldr is the only file/folder in there delete the /boot folder which holds it.

In sda2 you will see the last line
```
/Windows/System32/winload.exe /boot/grub/core.img
```
The entry /boot/grub/core.img should not be there.
I'm not 100% sure where this entry will be, but it could be in Windows/System32 folder. It could be an entry on its own, or it could be inside a folder called /boot. But be careful because Windows may need a /boot file of its ownin there! If you find a folder called /boot, open it up and if it just contains /grub/core.img (or /boot/grub/core.img) delete it.

I suspect that to do these jobs you will need to use ```
gksudo nautilus
```
maybe somebody could confirm/correct that please?

After the deletions please run ```
sudo update-grub
``` and then reboot and try Windows again.

---

### Post by Mark Phelps on 2011-01-24
The link below explains what Quackers has discovered:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows")

---

### Post by Enkh-Amgalan on 2011-01-26
Hi,

I fixed this problem. 

First, I repaired MBR using Windows 7 recovery disk. Then I had no grub menu, but I can booted windows.
Then, I deleted /grldr, /boot/grub/core.img. using ubuntu live CD.
Finally, I reinstalled grub.

After doing so I still had grub, Linux and Windows both worked.

Thanks

---

### Post by Rubi1200 on 2011-01-26
Excellent! Glad you got it sorted out :-)

---

### Post by Quackers on 2011-01-26
Very nice :-)
Will you mark the thread as solved please, using the Thread Tools near the top of the page. Thanks.

---

### Post by Enkh-Amgalan on 2011-01-27
Hi Quackers,

No problem. Tankhs again. :)

---

