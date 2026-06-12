---
title: "Ubuntu update stopped Vista working"
date: 2010-08-09
forum: General Help
---

### Post by danielz000 on 2010-08-09
Hi all,

My first post here... Any help with my problem is extremely appreciated...

Basically what seems to have happened is after the recent Ubuntu update my Windows partition became unbootable (or maybe just removed from Grub). This wasn't a problem for a while though as I still had access to my files through Ubuntu.

After a couple of weeks of using Ubuntu I needed to get into Windows, trying to (blindly) fix the problem I think what I did was open up Disk Manager in Ubuntu, clicked the Vista partition and marked it as bootable. Having done this some sort of error occured (can't remember what exactly) and after a reboot the partition is no longer accessible via Ubuntu.

I've read through a fair amount of similar posts and tried a number of solutions but haven't had any luck so I thought someone here might be able to shed a bit more light on to my situation?

Realistically, my main concern is getting data off the drive, if I can do that I can wipe the entire thing clean...

Thanks in advance for any help...

Daniel

---

### Post by davemike on 2010-08-09
Daniel...I'm also new to this forum. You can try following this[[http://ubuntuforums.org/showthread.php?t=1548330]](http://ubuntuforums.org/showthread.php?t=1548330]) link for more details.. they were discussing similar issues!!

---

### Post by danielz000 on 2010-08-09
Cheers Dave, just glancing through that thread it seemed that the user still had access to his Windows partition (which I don't).

There were also some notes about using a GParted bootable, so I might try burning that when I get home and seeing if it can do much with the drive...

---

### Post by Sef on 2010-08-09
> After a couple of weeks of using Ubuntu I needed to get into Windows, trying to (blindly) fix the problem I think what I did was open up Disk Manager in Ubuntu, clicked the Vista partition and marked it as bootable. Having done this some sort of error occured (can't remember what exactly) and after a reboot the partition is no longer accessible via Ubuntu.


You should have been able to boot into Vista before.  It would have been listed at the bottom of the GRUB start menu.  

Applications > Accessories > Terminal

then copy and paste this command:

```
sudo fdisk -l
```

Copy and paste the results here.

It will show us how your system is partitioned.

---

### Post by danielz000 on 2010-08-09
Hi Sef,

Thanks for your reply!

I'll get that command on this thread in about 5 hours. Sorry for the delay but I'm at work at the moment.

As for booting the partition, the option was available before the update. After the update it disappeared though. I still get a Windows 2000/XP option listed (I think that's some stupid Dell recovery tool), and a Windows Recovery Enviroment listed (which crashes when I pick it).

Any way, as requested, I'll get that information on here ASAP and if you (or anyone else) could take a look at it, that would be great!

Thanks,

Daniel

---

### Post by danielz000 on 2010-08-09
Hi All, 

The result of fdisk -l is as follows:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2   *          15        1320    10485760    7  HPFS/NTFS
/dev/sda3            1321       17262   128054115    7  HPFS/NTFS
/dev/sda4           17263       19458    17631978+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6           17263       19130    15004678+  83  Linux

Partition table entries are not in disk order

If anyone can make sense of that please help! 

Cheers,

Daniel

---

### Post by coldraven on 2010-08-09
Just a tip. If you accidentally choose the XP/2000 option it will overwrite Grub even if you select "Cancel" after it has finished booting up.
I got rid of mine as I had no wish to restore XP to its bloatware filled original state! 
If you really want to keep Vista I would recommend running it in a Virtual machine.
This is fairly easy to do although if you only have an OEM install disk you will need to read this link (this is for Virtualbox, I presume that there is something similar for other VMs)
This is because the Vista install is looking for a serial number and vendor details in your BIOS.

[http://www.virtualbox.org/manual/ch09.html#changedmi](http://www.virtualbox.org/manual/ch09.html#changedmi)

If you have an install disk with a serial number on it should be easier.

---

### Post by ccc2007chaos on 2010-08-09
hm... there's one thing i would suggest because i have been troubled many times with booting. try to install the "start up manager". you can find it in "ubuntu software center" when searching "grub". for me is the second result. after installing it, it'll appear in "System-Administration-Start up manager" menu. When you will open it, it's scanning the hard-drives for boot options ( this will also remove or add entries that have been deleted from the system or not created after installation ). hope that somehow works, but your problem really sounds strange. if someone else tell you something different, i think it's better to listen to him/her and not to me. my experience is through troubles :D 

good luck

---

### Post by danielz000 on 2010-08-09
hi CCC

I gave that a try but it didn't help unfortunately...

I must of totally destroyed my MBR last night when I was trying to fix the computer as I keep getting some grub interface/terminal thing now instead of the usual grub OS selection menu...

Doh!

---

### Post by danielz000 on 2010-08-09
Hi All,

I managed to save the partition using testdisk... I had to do a disk scan then a deep scan which eventually found the NTFS partition (which was marked as deleted). I changed it to P(rimary) and can now access the partition from Ubuntu.

Unfortunately I still can't boot Vista as it's not in the grub menu list. I followed a guide to edit the /boot/grub/menu.lst file but when that tried to load the vista partition it said the partition does not exist... I added something like hd(0,2) to the list... As my fdisk -l now reads:

/dev/sda1               1          14      112423+   6  FAT16
/dev/sda2            1320       17262   128052728+   7  HPFS/NTFS
/dev/sda3   *       17263       19130    15004676   83  Linux
/dev/sda4           19131       19458     2620416    c  W95 FAT32 

Unfortunately that didn't work... Can anyone point me in the write direction?

Cheers,

Daniel

---

### Post by mr clark25 on 2010-08-09
i had the exact same problem... up until the part about you not being able to view your files....

could you post the output of:
```

sudo update-grub

```


i got errors when trying to dual boot, and it turns out it was a known bug.

---

### Post by wilee-nilee on 2010-08-09
If you can post the bootscript in my signature in code tags as described.

---

### Post by danielz000 on 2010-08-09
Hi Mr Clark, 

Was the bug an Ubuntu 10 bug? My dual boot was working with v9...

sudo update-grub FYI:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Cheers,

Daniel

---

### Post by danielz000 on 2010-08-09
> **wilee-nilee said:**
> If you can post the bootscript in my signature in code tags as described.

Hi mate...

The file should be attached...

---

### Post by wilee-nilee on 2010-08-09
Here it is.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 292395357 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 292512989 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       224,909       224,847   6 FAT16
/dev/sda2          21,196,800   277,302,256   256,105,457   7 HPFS/NTFS
/dev/sda3    *    277,314,093   307,323,444    30,009,352  83 Linux
/dev/sda4         307,337,216   312,578,047     5,240,832   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0A0C                              vfat       DellUtility                   
/dev/sda2        8E8606A78606903F                       ntfs       OS                            
/dev/sda3        d0216ad3-4a54-4fd9-95a1-b2c1643b87e4   ext4                                     
/dev/sda4        340A-D50B                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev             /scratchbox/users/daniel/dev none       (rw,bind)
/dev/pts         /scratchbox/users/daniel/dev/pts none       (rw,bind)
/dev/shm         /scratchbox/users/daniel/dev/shm none       (rw,bind)


=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid		d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid		d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Chainload into GRUB 2
root		d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
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
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
	echo	'Loading Linux 2.6.31-17-generic ...'
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d0216ad3-4a54-4fd9-95a1-b2c1643b87e4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-0a0c
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod fat
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 340a-d50b
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d0216ad3-4a54-4fd9-95a1-b2c1643b87e4 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 142.1GB: boot/grub/core.img
 147.6GB: boot/grub/grub.cfg
 143.4GB: boot/grub/menu.lst
 142.4GB: boot/grub/stage2
 143.0GB: boot/initrd.img-2.6.31-17-generic
 143.0GB: boot/initrd.img-2.6.32-21-generic
 144.5GB: boot/vmlinuz-2.6.31-17-generic
 143.5GB: boot/vmlinuz-2.6.32-21-generic
 143.0GB: initrd.img
 143.0GB: initrd.img.old
 143.5GB: vmlinuz
 144.5GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768
```

---

### Post by danielz000 on 2010-08-09
Whoops! Sorry! I forgot to put it in code tags! I'm so damn tired! :( It's 1am and I had such a busy weekend! Apologise!

Does that file make much sense to you?

---

### Post by mas_sergio on 2010-08-09
thats scary I need windows. :shock:I hope this doesn't happen to me becuase I would be so lost. ](*,)

Sorry i can't help it must be frustrating. #-o

---

### Post by danielz000 on 2010-08-10
It is!

Hopefully someone will come to my rescue soon! ;)

---

### Post by danielz000 on 2010-08-10
bump

---

### Post by danielz000 on 2010-08-12
One last attempt and an update... I've managed to get grub and Ubuntu working fine. I've managed to remount my Windows partition and when I use my Windows Recovery Environment it detects Vista. I've also ran "Repair Boot Problems" (or something to that affect), bootrec with /fixmbr, /fixboot and /rebuildbcd but Windows still won't reboot...

Does anyone have any further ideas?

Is it possible that the boot process is hard coded to a particular partition or something?

Cheers,

Daniel

---

