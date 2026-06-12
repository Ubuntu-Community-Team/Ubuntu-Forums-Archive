---
title: "System not booting; unable to find boot drive"
date: 2010-09-07
forum: General Help
---

### Post by saasira on 2010-09-07
Hi,
 
I have upgraded a ubuntu virtual machine (run using virtual box, on windows) from 8.04 to 10.04. It worked fine for a few days after upgrade.
 
A few days ago I have upgrade the gnome to latest version because some security testing tool, ettercap and dnsmap required 2.2+ GTK. The system worked fine even after upgrading the GTK, but I think it did not boot up after I started the machine a couple of days later.
 
 
I tried all I could with my little knowledge of linux systems but could not get it up and running; so came here for help.
 
Here is the complete info regarding boot partitions of the system, given by boot_info_script.sh, a troubleshooting utility shell script hosted on sourceforge.net:
 
-----------------------------------------------------------------
 
```

 
Boot Info Script 0.55 dated February 15th, 2010 
 
============================= Boot Info Summary: ==============================
 
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 
sda1: _________________________________________________________________________
 
File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/menu.lst /etc/fstab
 
sda2: _________________________________________________________________________
 
File system: Extended Partition
Boot sector type: -
Boot sector info: 
 
sda5: _________________________________________________________________________
 
File system: swap
Boot sector type: -
Boot sector info: 
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 17.2 GB, 17179869184 bytes
255 heads, 63 sectors/track, 2088 cylinders, total 33554432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start End Size Id System
 
/dev/sda1 * 63 32,049,674 32,049,612 83 Linux
/dev/sda2 32,049,675 33,543,719 1,494,045 5 Extended
/dev/sda5 32,049,738 33,543,719 1,493,982 82 Linux swap / Solaris
 
 
blkid -c /dev/null: ____________________________________________________________
 
Device UUID TYPE LABEL 
 
/dev/loop0 squashfs 
/dev/sda1 9b6f64df-522f-4e00-8a5c-85d1c8e29150 ext3 
/dev/sda2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sda5 1d70293c-ac64-4be8-b34a-1cc7ad6b7081 swap 
/dev/sda: PTTYPE="dos" 
 
============================ "mount | grep ^/dev output: ===========================
 
Device Mount_Point Type Options
 
/dev/sda1 /mnt/target ext3 (rw)
 
 
=========================== sda1/boot/grub/menu.lst: ===========================
 
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.
 
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3
 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
 
# Pretty colours
#color cyan/blue white/blue
 
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
 
#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda1 ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
 
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true
 
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false
 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
 
## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false
 
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
 
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
 
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single
 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
 
## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect
 
## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
 
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
 
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
 
## ## End Default Options ##
 
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet
 
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.32-24-generic
 
title        Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-27-generic
quiet
 
title        Ubuntu 10.04.1 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.24-27-generic
 
title        Ubuntu 10.04.1 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet
 
### END DEBIAN AUTOMAGIC KERNELS LIST
 
=============================== sda1/etc/fstab: ===============================
 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
#UUID=9b6f64df-522f-4e00-8a5c-85d1c8e29150 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
#UUID=1d70293c-ac64-4be8-b34a-1cc7ad6b7081 none swap sw 0 0
 
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
 
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
 
=================== sda1: Location of files loaded by Grub: ===================
 
 
13.6GB: boot/grub/menu.lst
13.6GB: boot/grub/stage2
13.6GB: boot/initrd.img-2.6.24-27-generic
13.6GB: boot/initrd.img-2.6.24-27-generic.bak
13.5GB: boot/initrd.img-2.6.32-24-generic
13.5GB: boot/vmlinuz-2.6.24-27-generic
13.6GB: boot/vmlinuz-2.6.32-24-generic
13.5GB: initrd.img
13.6GB: initrd.img.old
13.6GB: vmlinuz
13.5GB: vmlinuz.old
=============================== StdErr Messages: ===============================
 
mdadm: No arrays found in config file or automatically
 
-----------------------------------------------------------------
 
A few more details:
 
root@PartedMagic:/mnt/target/home/saasira# ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Sep 7 23:38 1d70293c-ac64-4be8-b34a-1cc7ad6b7081 -> ../../sda5
lrwxrwxrwx 1 root root 10 Sep 7 23:38 9b6f64df-522f-4e00-8a5c-85d1c8e29150 -> ../../sda1
 
 
root@PartedMagic:/mnt/target/home/saasira# ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root 9 Sep 7 23:38 ata-VBOX_HARDDISK_VBa6742cd7-ed2f731d -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 7 23:38 ata-VBOX_HARDDISK_VBa6742cd7-ed2f731d-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 7 23:38 ata-VBOX_HARDDISK_VBa6742cd7-ed2f731d-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Sep 7 23:38 ata-VBOX_HARDDISK_VBa6742cd7-ed2f731d-part5 -> ../../sda5
lrwxrwxrwx 1 root root 9 Sep 7 23:38 scsi-SATA_VBOX_HARDDISK_VBa6742cd7-ed2f731d -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 7 23:38 scsi-SATA_VBOX_HARDDISK_VBa6742cd7-ed2f731d-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 7 23:38 scsi-SATA_VBOX_HARDDISK_VBa6742cd7-ed2f731d-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Sep 7 23:38 scsi-SATA_VBOX_HARDDISK_VBa6742cd7-ed2f731d-part5 -> ../../sda5
 
 
 
```
 
 
 
Although this is a virtual machine, I have got some important data in that system, and more over the development and testing environment I have setup in that VM is quite tedious and will take days, if not weeks to redo in case I cannot restore the system back to normal.
 
So, dear Linux masters, please help me get this issue fixed and restore the system back to its original state.
 
I hope I can get past this issue soon with the help of some Linux masters.
 
Thanks and Regards,
Samba

---

