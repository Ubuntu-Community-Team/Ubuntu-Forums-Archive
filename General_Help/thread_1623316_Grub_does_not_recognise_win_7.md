---
title: "Grub does not recognise win 7"
date: 2010-11-16
forum: General Help
---

### Post by Bob Fletcher on 2010-11-16
HI,
I have have just installed 10.10 on my Acer Aspire laptop. I connected to the Internet during installation and therefore should be right up to date.
Grub2 does not show Windows 7 as a boot option. Did a bit of searching and ran sudo update-grub2 but no success. I am a newbie as far as Ubuntu is concerned. I installed 9.04 on my netbook and that worked fine.
I have the added problem in having to get into Windows very shortly and I haven’t a clue how to do it if grub remains broken.
Thank you
Robert..
PS: Windows partition still there I have not deleted it.

---

### Post by Rubi1200 on 2010-11-16
Hi,
please boot into Ubuntu and run the boot info script linked at the bottom of my post.

Follow the instructions and post the results back here so we can advise you further.

Thanks.

---

### Post by Bob Fletcher on 2010-11-16
> **Rubi1200 said:**
> Hi,
please boot into Ubuntu and run the boot info script linked at the bottom of my post.

Follow the instructions and post the results back here so we can advise you further.

Thanks.
here is the results......
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   391,523,732   366,141,033   7 HPFS/NTFS
/dev/sda4         391,524,350   625,141,759   233,617,410   5 Extended
/dev/sda5         391,524,352   615,561,215   224,036,864  83 Linux
/dev/sda6         615,563,264   625,141,759     9,578,496  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D4548B35548B18FE                       ntfs       PQSERVICE                     
/dev/sda2        A4C48B81C48B5488                       ntfs       SYSTEM RESERVED               
/dev/sda3        D0220E0F220DFAEC                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        577a28e8-8121-4715-98e9-c846e2180dc5   ext4                                     
/dev/sda6        88bdae77-b1d8-4eac-b954-a28b99c43e8a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 577a28e8-8121-4715-98e9-c846e2180dc5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 577a28e8-8121-4715-98e9-c846e2180dc5
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 577a28e8-8121-4715-98e9-c846e2180dc5
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=577a28e8-8121-4715-98e9-c846e2180dc5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 577a28e8-8121-4715-98e9-c846e2180dc5
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=577a28e8-8121-4715-98e9-c846e2180dc5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 577a28e8-8121-4715-98e9-c846e2180dc5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 577a28e8-8121-4715-98e9-c846e2180dc5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 (on /dev/sda2)" {
insmod ntfs
set root=(hd1,1)
chainloader +1
}
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
UUID=577a28e8-8121-4715-98e9-c846e2180dc5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=88bdae77-b1d8-4eac-b954-a28b99c43e8a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 222.0GB: boot/grub/core.img
 301.5GB: boot/grub/grub.cfg
 291.0GB: boot/initrd.img-2.6.35-22-generic-pae
 222.0GB: boot/vmlinuz-2.6.35-22-generic-pae
 291.0GB: initrd.img
 222.0GB: vmlinuz

---

### Post by Jahid65 on 2010-11-16
Not grub2 , it is
```
sudo update-grub
```

---

### Post by Bob Fletcher on 2010-11-16
> **Jahid65 said:**
> Not grub2 , it is
```
sudo update-grub
```

just did that it made no difference.

---

### Post by Bob Fletcher on 2010-11-16
PLEASE PLEASE
I am in a real mess I must get into Windows even if it means loosing Ubuntu at this stage.
Just looked at the windows recovery disks and it want to reinstall the os. how do i get out of this mess.
robert

---

### Post by oldfred on 2010-11-16
The script looks normal. So I am suprised the osprober is not picking up windows. With Vista it usually reverses the recovery & install titles, but finds them.

It looks like you tried a manual boot stanza.But it needs to be hd0,2 for sda2.

menuentry "Windows 7 (on /dev/sda2)" {
insmod ntfs
set root=(hd1,1)
chainloader +1
}

Corrected:
menuentry "Windows 7 (on /dev/sda2)" {
 insmod ntfs
 set root=(hd0,2)
 chainloader +1
 }

but if osprober is not finding it, it may not still work.

If you have to run repairs:
oldfred's Windows repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by HarrisonNapper on 2010-11-16
Is Windows on an entirely separate hard drive? If so, you can use the boot selector on your computer to pick that hard drive and boot right to Windows (usually Esc or F10)

Cheers.

---

### Post by wojox on 2010-11-16
Have you tried this [How to fix Vista/Window 7 when the boot files are missing]("http://ubuntuforums.org/showthread.php?t=813628#4")

---

### Post by Bob Fletcher on 2010-11-16
> **oldfred said:**
> The script looks normal. So I am suprised the osprober is not picking up windows. With Vista it usually reverses the recovery & install titles, but finds them.

It looks like you tried a manual boot stanza.But it needs to be hd0,2 for sda2.
[snip]

Hi I had forgotten that I did that manual but I removed it when it would not work. I put in the code again and tried it and it worked. I am actually running under Windows now.
Thank you every one for your help. I want to try and gradually run in a Linux only environment but this may take some time.
Thanks
Robert...

---

### Post by Rubi1200 on 2010-11-17
Glad to hear you got it sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by Bob Fletcher on 2010-11-17
> **Rubi1200 said:**
> Glad to hear you got it sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.
Thanks I have done it. In the past I have all sorts of problems with Linux but never the boot loader. Thanks again to everyone for your help.

---

