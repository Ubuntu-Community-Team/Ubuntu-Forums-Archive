---
title: "Volume &quot;Boot&quot; message"
date: 2010-10-22
forum: General Help
---

### Post by noelc on 2010-10-22
Hi I upgraded to Ubuntu 10.10 today and when it finished I got this message The volume "Boot" has only MB disk remaining.

I know I,ve got plenty disk space.

Appreciate any help with this

---

### Post by Quackers on 2010-10-22
Please download the boot info script from the site below to your desktop. Then run it in a terminal using the command on that page. This will produce a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. (For code tags click on New Reply then on the # symbol in the toolbar and paste between them.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by noelc on 2010-10-23
> **Quackers said:**
> Please download the boot info script from the site below to your desktop. Then run it in a terminal using the command on that page. This will produce a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. (For code tags click on New Reply then on the # symbol in the toolbar and paste between them.

[SIZE="7"][SIZE="7"][http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Ok I,ve down loaded this but understand what you mean by running it?? Ive opened a terminal and pasted the command  sudo bash boot_info_script055.sh which is listed at the top of the page. But the message I get is no such file or directory? 

If I double click the Icon I get pages of output? I,m assuming this is not what you we to cut and pastes?

---

### Post by Quackers on 2010-10-23
If the boot script is on your desktop you need to open up a terminal (Applications > Accessories > Terminal and type in or copy/paste the command on that website ie

 sudo bash ~/Desktop/boot_info_script*.sh 

then enter your password and the sript will then produce the results.txt file.

---

### Post by noelc on 2010-10-23
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

md1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       192,779       192,717  fd Linux raid autodetect
/dev/sda2             192,780   976,768,064   976,575,285   5 Extended
/dev/sda5             192,843     8,000,369     7,807,527  82 Linux swap / Solaris
/dev/sda6           8,000,433   976,768,064   968,767,632  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       192,779       192,717  fd Linux raid autodetect
/dev/sdb2             192,780   976,768,064   976,575,285   5 Extended
/dev/sdb5             192,843     8,000,369     7,807,527  82 Linux swap / Solaris
/dev/sdb6           8,000,433   976,768,064   968,767,632  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         2c270fda-d49d-4cb0-8ee2-6b32936824b6   ext2                                     
/dev/md1         a4a547e4-d499-4ec2-9119-bc245ae0fddd   ext3                                     
/dev/sda1        85a93a16-93a1-b3dd-8245-623813e4882c   linux_raid_member                               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b52ce487-142e-4acc-8337-4e0aeed66d5f   swap                                     
/dev/sda6        eefdc9ca-bfd8-8649-3e9a-d16b4e3ed730   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        85a93a16-93a1-b3dd-8245-623813e4882c   linux_raid_member                               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ed908a4c-9b9e-415e-9424-9457d85d103e   swap                                     
/dev/sdb6        eefdc9ca-bfd8-8649-3e9a-d16b4e3ed730   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md1         /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/md0         /boot                    ext2       (rw,relatime)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=user1)


============================== md0/grub/menu.lst: ==============================

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
# kopt=root=/dev/md1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 10.10, kernel 2.6.35-22-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.35-22-generic root=/dev/md1 ro quiet splash 
initrd		/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.35-22-generic root=/dev/md1 ro  single
initrd		/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

==================== md0: Location of files loaded by Grub: ====================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

================================ md1/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/md1 during installation
UUID=a4a547e4-d499-4ec2-9119-bc245ae0fddd /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=2c270fda-d49d-4cb0-8ee2-6b32936824b6 /boot           ext2    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=b52ce487-142e-4acc-8337-4e0aeed66d5f none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=ed908a4c-9b9e-415e-9424-9457d85d103e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

==================== md1: Location of files loaded by Grub: ====================


    .0GB: initrd.img
    .0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 
```

---

