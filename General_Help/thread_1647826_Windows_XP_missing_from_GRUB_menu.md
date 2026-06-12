---
title: "Windows XP missing from GRUB menu"
date: 2010-12-17
forum: General Help
---

### Post by redfireplace on 2010-12-17
I've seen some other posts on the subject, but none solve my problem. I had Windows XP installed, then installed Ubuntu 9.10 in a different partition. I was able to choose which OS to boot. Then I did a distro update to 10.04. Now Windows is missing from the GRUB boot menu.

sudo update-grub doesn't change anything so I think sudo os-prober isn't finding Windows.

I've edited grub.cfg and can get an entry added for Windows, but it doesn't actually load Windows. It just reboots the machine. If I run sudo update-grub after adding a menuentry for Windows to grub.cfg, the menuentry I added disappears.

I've run testdisk, but BackupBS isn't an option. It says the original and backup boot sector are identical.

cfdisk says sda1 is the only partition that is NTFS and it is set to Boot.

I've already installed all available updates from lucid-security and lucid-updates.

I've run bootinfoscript and here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         122,881,185   625,137,344   502,256,160   5 Extended
/dev/sda5         122,881,248   619,129,034   496,247,787  83 Linux
/dev/sda6         619,129,098   625,137,344     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20485398528 bytes
255 heads, 63 sectors/track, 2490 cylinders, total 40010544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    40,001,849    40,001,787   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7EE8CE80E8CE3665                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0e1d0227-f753-4f7b-b28b-106e6f6c5ecb   ext4                                     
/dev/sda6        6b3af201-4dc1-4104-96d2-7cea762073bb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4927-53E5                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP (on /dev/sda1)" {
insmod ntfs
set root='(sda1,1)'
search --no-floppy --fs-uuid --set 7EE8CE8OE8CE3665
drivemap -s (sda1) ${root}
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6b3af201-4dc1-4104-96d2-7cea762073bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  64.3GB: boot/grub/core.img
 113.1GB: boot/grub/grub.cfg
  64.9GB: boot/initrd.img-2.6.31-22-generic
  65.0GB: boot/initrd.img-2.6.32-22-generic
  64.8GB: boot/initrd.img-2.6.32-23-generic
  66.6GB: boot/initrd.img-2.6.32-24-generic
  64.9GB: boot/initrd.img-2.6.32-25-generic
  64.9GB: boot/initrd.img-2.6.32-26-generic
  65.6GB: boot/vmlinuz-2.6.31-22-generic
  64.8GB: boot/vmlinuz-2.6.32-22-generic
  64.4GB: boot/vmlinuz-2.6.32-23-generic
  64.7GB: boot/vmlinuz-2.6.32-24-generic
  64.9GB: boot/vmlinuz-2.6.32-25-generic
  64.4GB: boot/vmlinuz-2.6.32-26-generic
  64.9GB: initrd.img
  64.9GB: initrd.img.old
  64.4GB: vmlinuz
  64.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

I've run out of ideas and now ask for help from the experts. btw, I have a 20 gig hard drive with Windows 98 on it, but that's not the drive I care about. Ignore that one. Ubuntu and Windows XP are both on the 320 gig drive. That's the one I care about.

---

### Post by oldfred on 2010-12-18
This is from mine:
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Yours is missing /ntdetect.com.

Your 40_custom shows hd1 or sdb as boot drive. It should be hd0 for sda.

I am posting the entire set of instructions but you should only need to copy ntdetect.com to your windows root c:\ folder. Two ways shown - from Win CD and from service pack files with Ubuntu.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
[COLOR=Red]COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\[/COLOR]
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to [COLOR=Red]C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. [/COLOR]

[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by Krytarik on 2010-12-18
The things are lot different with GRUB2, which Lucid uses by default.

Read this about the new structure: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

That's why your manually added menu entry gets deleted when running "sudo update-grub".

Hints:
- You have to add it to "/etc/grub.d/40_custom"
         - The first partition for GRUB 2 is **1**, not **0** (like it was in GRUB). Devices still start the count at **0**.

EDIT: Ok, forget about the first one, I'm still not too used to the output of the "Boot Info Script".

---

### Post by Krytarik on 2010-12-18
Your "/etc/grub.d/40_custom" should look like this, if I'm right:
```
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7EE8CE8OE8CE3665
chainloader +1
}

```You don't have to use the drivemap-command, because your Windows-installation resides on the first drive.

I'm not sure if you have to use the insmod and search options, try disabling them if boot fails.

---

### Post by redfireplace on 2010-12-24
Krytarik, I added your code to my /etc/grub.d/40_custom file. Now Windows is an option in the grub menu, but when I select it, Windows doesn't boot. I get an error message.```
error: cannot get C/H/S values
```
I've tried commenting out the two lines you suggested, both one at a time and together, but I get the same error. Is there anything else I can try?

---

### Post by wilee-nilee on 2010-12-24
> **redfireplace said:**
> Krytarik, I added your code to my /etc/grub.d/40_custom file. Now Windows is an option in the grub menu, but when I select it, Windows doesn't boot. I get an error message.```
error: cannot get C/H/S values
```
I've tried commenting out the two lines you suggested, both one at a time and together, but I get the same error. Is there anything else I can try?

Your answer is in post 2 grasshopper.

You are missing /ntdetect.com.

Follow the instructions on adding it back.

---

### Post by redfireplace on 2010-12-24
I can boot into Ubuntu, so I copied ntdetect.com into the root of c and rebooted. I still get the same error.```
error: cannot get C/H/S values
```
I reran bootinfoscript. Here is the output.```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sda2         122,881,185   625,137,344   502,256,160   5 Extended
/dev/sda5         122,881,248   619,129,034   496,247,787  83 Linux
/dev/sda6         619,129,098   625,137,344     6,008,247  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20485398528 bytes
255 heads, 63 sectors/track, 2490 cylinders, total 40010544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    40,001,849    40,001,787   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7EE8CE80E8CE3665                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0e1d0227-f753-4f7b-b28b-106e6f6c5ecb   ext4                                     
/dev/sda6        6b3af201-4dc1-4104-96d2-7cea762073bb   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4927-53E5                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 0e1d0227-f753-4f7b-b28b-106e6f6c5ecb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows XP (on /dev/sda1)" {
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7EE8CE8OE8CE3665
chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=0e1d0227-f753-4f7b-b28b-106e6f6c5ecb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6b3af201-4dc1-4104-96d2-7cea762073bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  64.3GB: boot/grub/core.img
  63.7GB: boot/grub/grub.cfg
  64.9GB: boot/initrd.img-2.6.31-22-generic
  65.0GB: boot/initrd.img-2.6.32-22-generic
  64.8GB: boot/initrd.img-2.6.32-23-generic
  66.6GB: boot/initrd.img-2.6.32-24-generic
  64.9GB: boot/initrd.img-2.6.32-25-generic
  64.9GB: boot/initrd.img-2.6.32-26-generic
  64.9GB: boot/initrd.img-2.6.32-27-generic
  65.6GB: boot/vmlinuz-2.6.31-22-generic
  64.8GB: boot/vmlinuz-2.6.32-22-generic
  64.4GB: boot/vmlinuz-2.6.32-23-generic
  64.7GB: boot/vmlinuz-2.6.32-24-generic
  64.9GB: boot/vmlinuz-2.6.32-25-generic
  64.4GB: boot/vmlinuz-2.6.32-26-generic
  64.8GB: boot/vmlinuz-2.6.32-27-generic
  64.9GB: initrd.img
  64.9GB: initrd.img.old
  64.8GB: vmlinuz
  64.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by wilee-nilee on 2010-12-25
If it was me I would want to know, can XP boot on its own from a ms bootloader in the mbr. Your grub customizing may have thrown a wrench in the whole thing when you you were just missing part of the XP boot.

---

### Post by threegremlins on 2010-12-27
i found reinstalling the same version of the already installed grub did the trick.

---

