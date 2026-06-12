---
title: "Grub/Windows 7 Issue"
date: 2010-06-12
forum: General Help
---

### Post by xkrazykidx on 2010-06-12
Hey everyone, first off I would like to say I LOVE (<3) Ubuntu 10.04 its the best Linux distro imho. I have been using Ubuntu since 7.10.

I would use Ubuntu as my main OS, but I I just cant seem to loose Windows because I always seem to need it. But beyond that I am trying to dual boot them in perfect Harmony. But after installing Windows 7 along time ago it decided to install to my D drive and I never bothered to fix it. Now I decided to install Ubuntu on my external drive to play around with again and get familiar with again for my Job. But Grub can not find the Windows destination. So I have 4 drives. 750GB, 250GB, 500GB, 250GBEX) Partitioned Fat32 and Ex3.

Im pretty sure I am using Grub2 as my loader. So heres my Boot Results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #4 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,465,127,999 1,465,127,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
31 heads, 14 sectors/track, 2250629 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdd1              40       409,639       409,600 System/Boot Partition
/dev/sdd2         411,648   244,552,272   244,140,625 Linux or Data
/dev/sdd3     244,553,728   248,459,263     3,905,536 Linux Swap
/dev/sdd4     248,459,264   488,396,799   239,937,536 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E8C0E235C0E20A20                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B6AC1D0FAC1CCC2D                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C2F2C8E6F2C8E031                       ntfs       XKRAZYKIDX                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        70D6-1701                              vfat       EFI                           
/dev/sdd2        FE04BC4B04BC0923                       ntfs                                     
/dev/sdd3        24a4c1a7-a788-4cbc-9432-caaac78af892   swap                                     
/dev/sdd4        23472cbe-314b-4daa-8463-9ef7fb32e52f   ext3                                     
/dev/sdd: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd4        /                        ext3       (rw,errors=remount-ro)
/dev/sdd2        /media/FE04BC4B04BC0923  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=================== sdd1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

=========================== sdd4/boot/grub/grub.cfg: ===========================

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
set root='(hd3,4)'
search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
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
set root='(hd3,4)'
search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
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
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=23472cbe-314b-4daa-8463-9ef7fb32e52f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=23472cbe-314b-4daa-8463-9ef7fb32e52f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e8c0e235c0e20a20
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set c2f2c8e6f2c8e031
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd4 during installation
UUID=23472cbe-314b-4daa-8463-9ef7fb32e52f /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdd3 during installation
UUID=24a4c1a7-a788-4cbc-9432-caaac78af892 none            swap    sw              0       0

=================== sdd4: Location of files loaded by Grub: ===================


 245.8GB: boot/grub/core.img
 245.9GB: boot/grub/grub.cfg
 245.8GB: boot/initrd.img-2.6.32-21-generic
 245.9GB: boot/vmlinuz-2.6.32-21-generic
 245.8GB: initrd.img
 245.9GB: vmlinuz
```




This is my Grub.cfg


```
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
set root='(hd3,4)'
search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
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
set root='(hd3,4)'
search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
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
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=23472cbe-314b-4daa-8463-9ef7fb32e52f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=23472cbe-314b-4daa-8463-9ef7fb32e52f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd3,4)'
	search --no-floppy --fs-uuid --set 23472cbe-314b-4daa-8463-9ef7fb32e52f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e8c0e235c0e20a20
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set c2f2c8e6f2c8e031
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

Any help would be greatly appreciated :)

---

### Post by MichealH on 2010-06-12
```
sudo update-grub
```? That should do.

Then do the ritual (Turn off then on)

---

### Post by xkrazykidx on 2010-06-12
> **MichealH said:**
> ```
sudo update-grub
```? That should do.

Then do the ritual (Turn off then on)

Thanks for the reply. Tried and When I clicked on Windows 7 Loader or Windows NT etc.. both dislplay can not find partition.

Im pretty sure my windows 7 is located on /dev/sdb1 but I dont know how to word it in grub.cfg

Also I think my MBR is located somewhere else though, so maybe thats whats confusing it...hmmm

---

### Post by prodigy_ on 2010-06-12
I assume the most simple solution in this case will be to try different values for **hdX** in the **set root** line of Windows 7 entry in grub.cfg.

Currently it's set **root='(hd[COLOR="Red"]2[/COLOR],1)'**. I'd say that ```
set root='(hd3,1)'
``` is most likely the correct line, so try this first.

---

### Post by xkrazykidx on 2010-06-12
> **prodigy_ said:**
> I assume the most simple solution in this case will be to try different values for **hdX** in the **set root** line of Windows 7 entry in grub.cfg.

Currently it's set **root='(hd[COLOR="Red"]2[/COLOR],1)'**. I'd say that ```
set root='(hd3,1)'
``` is most likely the correct line, so try this first.

Hey thanks for the reply, tried and it displayed "non System disk please reboot"

---

### Post by prodigy_ on 2010-06-12
Hmm. Try ```
set root='(hd1,1)'
```

If this doesn't work either then... broken MBR or (more likely) wrong BCD perhaps? To fix this boot from Win7 DVD into recovery console and use ```
bootrec.exe /scanos
``` command. It should help to identify the problem.

In any case, to restore MBR use (from Win7 recovery console): ```
bootrec.exe /fixmbr
``` and to reconfigure BCD:
```
bootrec.exe /rebuildbcd
```

However, after **bootrec /fixmbr** you'll most probably need to reinstall Grub (if you want to be able to boot into Ubuntu).

---

### Post by xkrazykidx on 2010-06-12
> **prodigy_ said:**
> Hmm. Try ```
set root='(hd1,1)'
```

If this doesn't work either then... broken MBR or (more likely) wrong BCD perhaps? To fix this boot from Win7 DVD into recovery console and use ```
bootrec.exe /scanos
``` command. It should help to identify the problem.

In any case, to restore MBR use (from Win7 recovery console): ```
bootrec.exe /fixmbr
``` and to reconfigure BCD:
```
bootrec.exe /rebuildbcd
```

However, after **bootrec /fixmbr** you'll most probably need to reinstall Grub (if you want to be able to boot into Ubuntu).

Hmm I tried hd1,1 didn't work so I put in my Win 7 recovery DVD. Clicked command prompt. Types bootrec.exe /scanos. 

It says total identified windows installations: 0

I'm currently on my iPhone so I will leave command prompt open 

Also if I reboot with the DVD in my drive and I don't press any keys the windows MBR displays. Do you think I should just reinstall Windows (which I hope I don't have to)

---

### Post by prodigy_ on 2010-06-12
> **xkrazykidx said:**
> It says total identified windows installations: 0

That's probably due to Grub2 in the MBRs of your HDDs. Well, if you want a relatively simple solution without any OS reinstallations, then 
```
bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /rebuildbcd
``` command sequence should help. But, like I said, after that you'll temporarily lose the ability to boot into your Ubuntu installation. So later you'll need to boot from Ubuntu Live CD and reinstall Grub (and hopefully then everything will work. :-)

---

### Post by xkrazykidx on 2010-06-12
> **prodigy_ said:**
> That's probably due to Grub2 in the MBRs of your HDDs. Well, if you want a relatively simple solution without any OS reinstallations, then 
```
bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /rebuildbcd
``` command sequence should help. But, like I said, after that you'll temporarily lose the ability to boot into your Ubuntu installation. So later you'll need to boot from Ubuntu Live CD and reinstall Grub (and hopefully then everything will work. :-)

Hmmm tried and I rebooted took out the disc and Grub displayed again so I rebooted with disk in tray but didn't press any buttons and windows MBR displayed so I need the disc in order to run windows....

---

### Post by oldfred on 2010-06-12
Your windows 7 install is on sdb, But you boot either thru sda or sdc. Your sda looks like it also has XP but is then missing the /Boot/BCD and has a grub4dos file /grldr.

You also have GPT partitioning on sdd. Supposedly with the system boot partition grub will install to sdd and use the boot partition for part of its files. I am not sure if it has to be called a BIOS boot partition and not just be a partition. It may need an extra module to use the GPT. I prefer to have grub on the same drive as the install.

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

