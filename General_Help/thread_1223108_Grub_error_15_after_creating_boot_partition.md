---
title: "Grub error 15 after creating boot partition"
date: 2009-07-25
forum: General Help
---

### Post by Justcameron on 2009-07-25
Hey all,

Running intrepid, I was getting grub error 18 because my kernel was too far along in the disk (no separate boot partition) so I created a 500MB boot partition at the start of the disk. 

Now whenever I boot I get 

[B]Grub Loading stage1.5.
GRUB loading, please wait...
Error 15[/B]

I have a Hardy liveCD which I am using to troubleshoot the problem.

Some information:
```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x871c871c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfeab794f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          65      522081   83  Linux
/dev/sdb2              66       60801   487861920    f  W95 Ext'd (LBA)
/dev/sdb5              66       19187   153597433+  83  Linux
/dev/sdb6           19188       19824     5116671   82  Linux swap / Solaris
/dev/sdb7           19825       60801   329147721    7  HPFS/NTFS

```
/dev/sdb1 is the boot partition. 
/dev/sdb5 is the / partition.

I moved the /boot folder on /dev/sdb5 to /boot.old and created a new empty folder /boot which /dev/sdb1 is supposed to mount to

fstab:
```
# /etc/fstab: static file system information.
#
# <file system>                            <mount point>               <type>       <options>                     <dump>  <pass>
proc                                       /proc                       proc         defaults                           0  0  
/dev/sdb1                                  /boot                       ext3         relatime,errors=remount-ro         0  2
/dev/sdb5                                  /                           ext3         relatime,errors=remount-ro         0  1  
/dev/sdb6                                  none                        swap         sw                                 0  0  
/dev/scd0                                  /media/cdrom0               udf,iso9660  user,noauto,exec,utf8              0  0  
/dev/fd0                                   /media/floppy0              auto         rw,user,noauto,exec,utf8           0  0  
/dev/sda1                                  /media/c                    ntfs         rw,auto,user,fmask=0111,dmask=0000 0  0
/dev/sdb7                                  /media/shared               ntfs         rw,auto,user,fmask=0111,dmask=0000 0  0  
none                                       /proc/bus/usb               usbfs        auto,busgid=129,busmode=0775,devgid=129,devmode=0664  0  0

```

```
sudo blkid
/dev/sda1: UUID="5E80E88E80E86DC9" LABEL="c" TYPE="ntfs" 
/dev/sdb1: UUID="ba118447-3c21-47fa-8e6d-453d1bf126b1" TYPE="ext3" 
/dev/sdb5: UUID="32674fa8-73f9-4be7-82c9-c1ce76bbf16e" TYPE="ext3" 
/dev/sdb6: UUID="5ab33a48-3ead-4b70-b40e-d5cccc5baf30" TYPE="swap" 
/dev/sdb7: UUID="01C906BB19213EF0" LABEL="Shared" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
```

menu.lst:
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
# kopt=root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd1,0)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro quiet splash 
initrd		/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro  single
initrd		/initrd.img-2.6.27-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Any help would be much appreciated!

---

### Post by lindsay7 on 2009-07-26
Try changing your bios to boot to your other disk drive first.

---

### Post by Justcameron on 2009-07-26
Boot info generated with boot_info_script032.sh
[http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and
                       looks at sector 755777 of the same hard drive for the
                       stage2 file. A stage2 file is at this location on
                       /dev/sdb. Stage2 looks on partition #1 for
                       /grub/menu.lst.
    Operating System: 
    Boot files/dirs:   /grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x871c871c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfeab794f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,044,224     1,044,162  83 Linux
/dev/sdb2           1,044,225   976,768,064   975,723,840   f W95 Ext d (LBA)
/dev/sdb5           1,044,288   308,239,154   307,194,867  83 Linux
/dev/sdb6         308,239,218   318,472,559    10,233,342  82 Linux swap / Solaris
/dev/sdb7         318,472,623   976,768,064   658,295,442   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5E80E88E80E86DC9" LABEL="c" TYPE="ntfs"
/dev/sdb1: UUID="ba118447-3c21-47fa-8e6d-453d1bf126b1" TYPE="ext3"
/dev/sdb5: UUID="32674fa8-73f9-4be7-82c9-c1ce76bbf16e" TYPE="ext3"
/dev/sdb6: TYPE="swap" UUID="5ab33a48-3ead-4b70-b40e-d5cccc5baf30"
/dev/sdb7: UUID="01C906BB19213EF0" LABEL="Shared" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb5 on /media/root type ext3 (rw)
/dev/sdb1 on /media/root/boot type ext3 (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

============================= sdb1/grub/menu.lst: =============================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        2

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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-14-generic
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro quiet splash
initrd        /initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro  single
initrd        /initrd.img-2.6.27-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=================== sdb1: Location of files loaded by Grub: ===================


    .3GB: grub/menu.lst
    .3GB: grub/stage2
    .0GB: initrd.img-2.6.27-14-generic
    .0GB: vmlinuz-2.6.27-14-generic

=========================== sdb5/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        2

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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-14-generic
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro quiet splash
initrd        /initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro  single
initrd        /initrd.img-2.6.27-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system>                            <mount point>               <type>       <options>                     <dump>  <pass>
proc                                       /proc                       proc         defaults                           0  0 
/dev/sdb1                                  /boot                       ext3         relatime,errors=remount-ro         0  2
/dev/sdb5                                  /                           ext3         relatime,errors=remount-ro         0  1 
/dev/sdb6                                  none                        swap         sw                                 0  0 
/dev/scd0                                  /media/cdrom0               udf,iso9660  user,noauto,exec,utf8              0  0 
/dev/fd0                                   /media/floppy0              auto         rw,user,noauto,exec,utf8           0  0 
/dev/sda1                                  /media/c                    ntfs         rw,auto,user,fmask=0111,dmask=0000 0  0
/dev/sdb7                                  /media/shared               ntfs         rw,auto,user,fmask=0111,dmask=0000 0  0 
none                                       /proc/bus/usb               usbfs        auto,busgid=129,busmode=0775,devgid=129,devmode=0664  0  0


=================== sdb5: Location of files loaded by Grub: ===================


    .9GB: boot/grub/menu.lst
    .9GB: boot/grub/stage2
    .5GB: boot/initrd.img-2.6.27-14-generic
    .5GB: boot/vmlinuz-2.6.27-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz

```
Help?

---

### Post by Justcameron on 2009-07-26
I changed the bios to boot the other disk first and get the amazingly helpful:

Error loading operating system

:(

---

### Post by lindsay7 on 2009-07-26
Try this and see if it helps.

Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by Justcameron on 2009-07-26
```
grub> find /boot/grub/stage1

Error 15: File not found
```

Thanks for your continued help!

---

### Post by swerdna on 2009-07-26
I wonder, did you put any kernel, initrd and so on in the new boot partition? ==> What files are in the partition /dev/sdb1?

Mount it in the live CD, maybe like this:
sudo mkdir /mnt/sdb1
sudo mount dev/sdb1 /mnt/sdb1
sudo ls -l /mnt/sdb1

---

### Post by lindsay7 on 2009-07-26
When you use the commands that I gave you, you need to make sure that the drives are mounted or the live cd will not see them. Go to Places/computer and right click on the drives to be sure that they are mounted and try running the commands again.

---

### Post by SoftwareExplorer on 2009-07-26
From this> **Justcameron said:**
> Boot info generated with boot_info_script032.sh
[http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and
                       looks at sector 755777 of the same hard drive for the
                       stage2 file. A stage2 file is at this location on
                       /dev/sdb. Stage2 looks on partition #1 for
                       /grub/menu.lst.
    Operating System: 
    Boot files/dirs:   /grub/menu.lst

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files/dirs:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x871c871c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfeab794f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,044,224     1,044,162  83 Linux
/dev/sdb2           1,044,225   976,768,064   975,723,840   f W95 Ext d (LBA)
/dev/sdb5           1,044,288   308,239,154   307,194,867  83 Linux
/dev/sdb6         308,239,218   318,472,559    10,233,342  82 Linux swap / Solaris
/dev/sdb7         318,472,623   976,768,064   658,295,442   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5E80E88E80E86DC9" LABEL="c" TYPE="ntfs"
/dev/sdb1: UUID="ba118447-3c21-47fa-8e6d-453d1bf126b1" TYPE="ext3"
/dev/sdb5: UUID="32674fa8-73f9-4be7-82c9-c1ce76bbf16e" TYPE="ext3"
/dev/sdb6: TYPE="swap" UUID="5ab33a48-3ead-4b70-b40e-d5cccc5baf30"
/dev/sdb7: UUID="01C906BB19213EF0" LABEL="Shared" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb5 on /media/root type ext3 (rw)
/dev/sdb1 on /media/root/boot type ext3 (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

============================= sdb1/grub/menu.lst: =============================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        2

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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-14-generic
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro quiet splash
initrd        /initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro  single
initrd        /initrd.img-2.6.27-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=================== sdb1: Location of files loaded by Grub: ===================


    .3GB: grub/menu.lst
    .3GB: grub/stage2
    .0GB: initrd.img-2.6.27-14-generic
    .0GB: vmlinuz-2.6.27-14-generic

=========================== sdb5/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        2

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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-14-generic
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro quiet splash
initrd        /initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root        (hd1,0)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=32674fa8-73f9-4be7-82c9-c1ce76bbf16e ro  single
initrd        /initrd.img-2.6.27-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system>                            <mount point>               <type>       <options>                     <dump>  <pass>
proc                                       /proc                       proc         defaults                           0  0 
/dev/sdb1                                  /boot                       ext3         relatime,errors=remount-ro         0  2
/dev/sdb5                                  /                           ext3         relatime,errors=remount-ro         0  1 
/dev/sdb6                                  none                        swap         sw                                 0  0 
/dev/scd0                                  /media/cdrom0               udf,iso9660  user,noauto,exec,utf8              0  0 
/dev/fd0                                   /media/floppy0              auto         rw,user,noauto,exec,utf8           0  0 
/dev/sda1                                  /media/c                    ntfs         rw,auto,user,fmask=0111,dmask=0000 0  0
/dev/sdb7                                  /media/shared               ntfs         rw,auto,user,fmask=0111,dmask=0000 0  0 
none                                       /proc/bus/usb               usbfs        auto,busgid=129,busmode=0775,devgid=129,devmode=0664  0  0


=================== sdb5: Location of files loaded by Grub: ===================


    .9GB: boot/grub/menu.lst
    .9GB: boot/grub/stage2
    .5GB: boot/initrd.img-2.6.27-14-generic
    .5GB: boot/vmlinuz-2.6.27-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz

```
 If he had a separate /boot would it be ```
grub> find /grub/stage1
```
 instead? Just a guess.

---

### Post by swerdna on 2009-07-26
> **SoftwareExplorer said:**
> From this If he had a separate /boot would it be ```
grub> find /grub/stage1
```
 instead? Just a guess.

That's why we need to see:> ls -l /mnt/sdb1

---

### Post by oldfred on 2009-07-26
When you inserted the /boot partition are the beginning of the disk every partition was renumbered and had to be edited in your new menu.lst.
Grub help here:
[http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368) it says:
- Error 15: this means that one of the files you specified (e.g. vmlinuz or initrd.img could not be found). So recheck the file names you entered are correct and located in the /boot directory.

Do you have the correct/same versions in your menu.lst and in /boot/grub?

---

