---
title: "gone in 60 seconds"
date: 2009-09-13
forum: General Help
---

### Post by darkreaction on 2009-09-13
After reinstalling grub after I installed an xp partition. I dont have the choice of booting xp. any help would be great! I am using Intrepid 8.10.

---

### Post by presence1960 on 2009-09-13
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by darkreaction on 2009-09-13
what exactly is the boot info script for

---

### Post by overdrank on 2009-09-13
Threads merged.

---

### Post by darkreaction on 2009-09-13
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda1 and 
                       looks at sector 49315919 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbce2081

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,848,037,274 1,848,037,212  83 Linux
/dev/sda2       1,848,037,275 1,953,503,999   105,466,725   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="fcad7196-506b-460c-bb18-5bc825e87c02" TYPE="ext3" 
/dev/sda2: UUID="B8FCA330FCA2E838" TYPE="ntfs" 
/dev/sdb1: LABEL="Cruzer" UUID="3820-4CF8" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andrew/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andrew)
/dev/scd1 on /media/MECH4VEN_1 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)
/dev/sdb1 on /media/Cruzer type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=fcad7196-506b-460c-bb18-5bc825e87c02 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fcad7196-506b-460c-bb18-5bc825e87c02

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		fcad7196-506b-460c-bb18-5bc825e87c02
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=fcad7196-506b-460c-bb18-5bc825e87c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		fcad7196-506b-460c-bb18-5bc825e87c02
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=fcad7196-506b-460c-bb18-5bc825e87c02 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		fcad7196-506b-460c-bb18-5bc825e87c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fcad7196-506b-460c-bb18-5bc825e87c02 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		fcad7196-506b-460c-bb18-5bc825e87c02
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fcad7196-506b-460c-bb18-5bc825e87c02 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		fcad7196-506b-460c-bb18-5bc825e87c02
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows xp
root		(hd0,0)
makeactive
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fcad7196-506b-460c-bb18-5bc825e87c02 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=1b0e14e3-a801-423c-bdd3-d6b2f87e5510 none            swap    sw              0       0
# /dev/sdb6
UUID=c741a84a-feb7-4010-8b9f-1ef5882421d7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

#Make USB Work in Sun VirtualBox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

=================== sda1: Location of files loaded by Grub: ===================


  25.2GB: boot/grub/menu.lst
  25.2GB: boot/grub/stage2
  25.2GB: boot/initrd.img-2.6.27-14-generic
  25.3GB: boot/initrd.img-2.6.27-7-generic
  25.2GB: boot/vmlinuz-2.6.27-14-generic
  25.3GB: boot/vmlinuz-2.6.27-7-generic
  25.2GB: initrd.img
  25.3GB: initrd.img.old
  25.2GB: vmlinuz
  25.3GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by presence1960 on 2009-09-13
Boot into ubuntu. Open a terminal by going Applications > Accessories > Terminal. Run this command in terminal ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

scroll down to this:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

title      Windows xp
root       (hd0,0)
makeactive
chainloader +1
```
 and change it to this:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows xp
rootnoverify (hd0,1)
chainloader  +1
```
 Click save on the toolbar at top. Close file & reboot. Try booting into windows without the flash drive plugged in.

---

