---
title: "Windows 7 &amp; Kubuntu 10.10 GRUB problem"
date: 2011-04-05
forum: General Help
---

### Post by claythearc on 2011-04-05
I had my Laptop, a Dell Inspiron 1520, running Windows 7 and Windows XP - I had a few gigs of unallocated space, so I decided to install Kubuntu alongside it, worked fine no problem, with the exception of running out of space very quickly - I got fed up with it, and installed Kubuntu over the Windows XP partition (around 80gigs, and the first OS to be installed on the computer). After I installed it, all was working perfectly until I rebooted to discover I am missing my Windows 7 boot option in GRUB, before I had to press Windows XP Embedded and it opened the boot dialog, but here I dont get the option, is there a GRUB 2 option I can change to allow it to show Windows 7?

P.S. The Computer works perfectly, it's just the GRUB doesn't show Windows 7, and I'm hesitant to format its old partition and reinstall it due to the fact that it may over ride the grub and leave me without Kubuntu access, any suggestions?

---

### Post by Hedgehog1 on 2011-04-05
claythearc,

Would you please do this so we can see what may be Happening:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.



***The Hedge***

:KS

---

### Post by wilee-nilee on 2011-04-05
+1 on the bootscript, if you had XP then installed W7 their boot was intertwined. You will need a W7 recovery or install disc to fix this, here is a recovery download.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

The script will confirm what is up, and where everything is at.

---

### Post by claythearc on 2011-04-05
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

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

/dev/sda1                  63       176,714       176,652  de Dell Utility
/dev/sda2    *        176,715   165,630,149   165,453,435  83 Linux
/dev/sda3         165,632,000   222,273,535    56,641,536   7 HPFS/NTFS
/dev/sda4         222,275,401   234,440,703    12,165,303   5 Extended
/dev/sda5         222,275,403   227,512,529     5,237,127  dd Dell Media Direct
/dev/sda6         227,514,368   234,440,703     6,926,336  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-031A                              vfat       DellUtility                   
/dev/sda2        e23a67de-f4ec-4056-9f5c-0119ea4360c9   ext4                                     
/dev/sda3        98C659C6C659A4F2                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        07D8-031A                              vfat       MEDIADIRECT                   
/dev/sda6        c15466db-526e-4d8d-a4de-a74c211f3f82   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e23a67de-f4ec-4056-9f5c-0119ea4360c9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=e23a67de-f4ec-4056-9f5c-0119ea4360c9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e23a67de-f4ec-4056-9f5c-0119ea4360c9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e23a67de-f4ec-4056-9f5c-0119ea4360c9 ro single 
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
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set e23a67de-f4ec-4056-9f5c-0119ea4360c9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 07d8-031a
	drivemap -s (hd0) ${root}
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  68.9GB: boot/grub/core.img
  13.4GB: boot/grub/grub.cfg
   5.8GB: boot/initrd.img-2.6.35-22-generic
   5.8GB: boot/initrd.img-2.6.35-28-generic
  69.0GB: boot/vmlinuz-2.6.35-22-generic
  68.9GB: boot/vmlinuz-2.6.35-28-generic
   5.8GB: initrd.img
   5.8GB: initrd.img.old
  68.9GB: vmlinuz
  69.0GB: vmlinuz.old

================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768


```

---

### Post by Hedgehog1 on 2011-04-05
As happens with *annoying regularity*, **wilee-nilee** is right. :D

It looks like the 'cheapest' way out of this is the do a FIXMBR from the Windows 7 rescue disk, and then update grub from the LiveCD/LiveUSB.

We can then talk about the leftover space from the XP partiton that didn't get removed/overwritten.

Would you like instructions for these two steps?

***The Hedge***

:KS

---

### Post by wilee-nilee on 2011-04-05
> **Hedgehog1 said:**
> As happens with *annoying regularity*, **wilee-nilee** is right. :D

It looks like the 'cheapest' way out of this is the do a FIXMBR from the Windows 7 rescue disk, and then update grub from the LiveCD/LiveUSB.

We can then talk about the leftover space from the XP partiton that didn't get removed/overwritten.

Would you like instructions for these two steps?

***The Hedge***

:KS

No your always right:) don't forget to move the bootflag to sda3

---

### Post by Hedgehog1 on 2011-04-05
> **wilee-nilee said:**
> No your always right :) don't forget to move the bootflag to sda3

I am not always right - Ask my wife... :P

---

### Post by Hedgehog1 on 2011-04-05
Updating the MBR to boot from Windows:

If you are unable to make a recovery disk, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by claythearc on 2011-04-05
thanks! so using the FIXMBR will not cause either OS to be overwritten correct, just a bit of space to be floating around due to magic?

---

### Post by Hedgehog1 on 2011-04-05
Then to update grub:

Please boot off the LiveCD/Live USB, select 'TRY', and then:

**EDIT:** *here wilee-nilee reminded me, and I still forgot:*

Using gparted, right click on the /dev/sda3 partition, edit flags and 'click' the boot flag.  This makes your windows 7 partition bootable directly.  It will look like this:

[IMG]http://img855.imageshack.us/img855/6408/bootflaggparted.png[/IMG]

You may need to press the 'check mark' button on the menu bar to make the change 'real'.


**NEXT:**

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:

```
sudo mount /dev/sda2 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```



You can now reboot, and you should see Windows and Ubuntu in the grub menu.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-05
> **claythearc said:**
> thanks! so using the FIXMBR will not cause either OS to be overwritten correct, just a bit of space to be floating around due to magic?

It updates the Master Boot Record to think like Windows 7 insted of XP.  *No OS is harmed in the running of this command.*

We then update it further to have it call grub and multi boot.

***The Hedge***

:KS

---

### Post by claythearc on 2011-04-09
Kubuntu or ubuntu refuses to boot from livecd now. Been like 20monutes

---

### Post by claythearc on 2011-04-09
Kubuntu or ubuntu refuses to boot from livecd now. Been like 20monutes

i recieve error stdin 0 repeatedly and when i boot to where grub would be normally, i get operating system missing. please help.

---

