---
title: "Please help me Configure GRUB"
date: 2009-06-29
forum: General Help
---

### Post by xCel on 2009-06-29
I just installed Vista on a separate partition, as well as running XP and Ubuntu on other partitions. I have 3 hard drives, the first one has 1 partition, the second has 1, and the 3rd has 3: 1 NFTS, 1 exp3, 1 swap.

Grub loads first, and gives me the option of choosing between linux or XP. I choose the XP, and it loads Vista... :) I know theres something wrong within menu.lst that is pointing to the wrong partition. 

Here is the output of the boot script:
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /NTLDR /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /boot/bcd 
                       /BOOT/bcd /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD 
                       /grldr /GRLDR /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99999999

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6bf8890e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   969,924,374   969,924,312   7 HPFS/NTFS
/dev/sdb2    *    969,924,375 1,412,643,644   442,719,270  83 Linux
/dev/sdb3       1,412,643,645 1,465,144,064    52,500,420  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c22076d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    42,186,689    42,186,627   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="CEF8637AF8635FA7" TYPE="ntfs" 
/dev/sdb1: UUID="173BE00400697C1E" TYPE="ntfs" 
/dev/sdb2: UUID="294b73ba-8198-460f-bb0e-cba5e2bfece5" TYPE="ext3" 
/dev/sdb3: UUID="ba85cc58-da57-440d-bd9b-548b1c992d9e" TYPE="swap" 
/dev/sdc1: LABEL="^J^J^J^J^J^J^J^J^J^J^J" UUID="1ADB-201A" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ian)


=========================== sdb2/boot/grub/menu.lst: ===========================

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
default		9

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=294b73ba-8198-460f-bb0e-cba5e2bfece5

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
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		FreeDOS
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
#title		Windows XP (hd1)
#rootnoverify	(hd1,0)
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1

title		Windows XP x64 Professional Edition
rootnoverify 	(hd2,0)
map 		(hd0) (hd2)
map		(hd2) (hd0)
chainloader 	+1

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc3
UUID=ba85cc58-da57-440d-bd9b-548b1c992d9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 600.7GB: boot/grub/menu.lst
 600.8GB: boot/grub/stage2
 600.8GB: boot/initrd.img-2.6.27-11-generic
 600.7GB: boot/initrd.img-2.6.27-14-generic
 600.8GB: boot/initrd.img-2.6.27-7-generic
 600.8GB: boot/vmlinuz-2.6.27-11-generic
 600.8GB: boot/vmlinuz-2.6.27-14-generic
 600.8GB: boot/vmlinuz-2.6.27-7-generic
 600.7GB: initrd.img
 600.8GB: initrd.img.old
 600.8GB: vmlinuz
 600.8GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /NOEXECUTE=OPTIN /FASTDETECT

c:\FREEDOS.BSS="FreeDOS" 


================================ sdc1/BOOT.INI: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /NOEXECUTE=OPTIN /FASTDETECT

c:\FREEDOS.BSS="FreeDOS" 

```


and here is what my Menu.lst looks like:

```
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
default		9

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=294b73ba-8198-460f-bb0e-cba5e2bfece5

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
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=294b73ba-8198-460f-bb0e-cba5e2bfece5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		294b73ba-8198-460f-bb0e-cba5e2bfece5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		FreeDOS
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title		Windows XP x64 Professional Edition
rootnoverify 	(hd2,0)
map 		(hd0) (hd2)
map		(hd2) (hd0)
chainloader 	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
#title		Windows XP (hd1)
#rootnoverify	(hd1,0)
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1
```

---

### Post by mhgsys on 2009-06-29
in a terminal or console;

```

sudo nano /boot/grub/menu.lst

```

uncomment the lines by removing the # in front of it
so :
```

#title		Windows XP (hd1)
#rootnoverify	(hd1,0)
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1

```

Will be 
```

title		Windows XP (hd1)
rootnoverify	(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```


and change 
```

title		Windows XP x64 Professional Edition
rootnoverify 	(hd2,0)
map 		(hd0) (hd2)
map		(hd2) (hd0)
chainloader 	+1

```

to something you like f.e 
```

title		Windows Vista
rootnoverify 	(hd2,0)
map 		(hd0) (hd2)
map		(hd2) (hd0)
chainloader 	+1

```

reboot, test it.

---

### Post by xCel on 2009-06-29
The last entry in Menu.lst is actually not correct. I put it there just to start.

I am having a hard time in figuring out how to tell GRUB how to look/boot from a certain partition and hard drive.

I am assuming its hard drive 2 (0,1,2)
Its on the first partition of drive 2 ( or is it the 0th partition?)

Ie, what do I put here so when I select Vista, it goes to my 3rd hard drive and 1st partition?
-----
map 		(hd0) (hd2)
map		(hd2) (hd0)

I dont understand why there are 4 entry points.

---

### Post by xCel on 2009-06-29
Can someone please help?

How do I point grub to point to the 3rd hard drive, 1st partition for Windows Vista and point to 2nd hard drive 1st partition to XP?

---

### Post by oldfred on 2009-06-30
I believe mhgsys has it correct. GRUB numbers drives and partitions one less that linux, or it starts counting from zero.
So in menu.lst for Grub hd0,0 is linux drive 1 or sda. linux drive sdc will be hd2 in grub.  
The map command is to switch the actual drive to drive 0 as windows wants to be on drive 0. All installs of windows in upper drives need to be mapped back to zero.

---

