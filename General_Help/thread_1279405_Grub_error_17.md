---
title: "Grub error 17"
date: 2009-09-30
forum: General Help
---

### Post by frilock on 2009-09-30
ok let me first say what i did :( i had some partitions that i wanted to merge so i used partition magic but the strange thing is that i messed with settings but didnt tell the program to go threw with them after i rebooted i would only get error 17  so i tried to fix the mbr and i got the grub back i can boot into windows fine but linux wont mount if i load a live cd i can see all my files some one please help me bellow is a copy of my  sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef70ef70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29157974    14578956    b  W95 FAT32
/dev/sda2        29157975   976768064   473805045    f  W95 Ext'd (LBA)
/dev/sda5        29158038    57095009    13968486   83  Linux
/dev/sda6        57095073    83827169    13366048+  83  Linux
/dev/sda7        83827233   940332644   428252706   83  Linux
/dev/sda8       940332708   952477784     6072538+  82  Linux swap / Solaris
/dev/sda9       952477848   964622924     6072538+  82  Linux swap / Solaris
/dev/sda10      964622988   976768064     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x145de75e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 512 MB, 512753664 bytes
16 heads, 32 sectors/track, 1956 cylinders, total 1001472 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfb8bfb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     1001471      500720    b  W95 FAT32
ubuntu@ubuntu:~$ sudo gedit /boot/grub/menue.1st

---

### Post by frilock on 2009-09-30
bump...... i downloaded super grub and it says something about multiple calmed blocks on dev/sda5 some one please give me a hand

---

### Post by oldfred on 2009-09-30
Please download this scrip, run it &  post the results.
It will tell us what partitions are bootable and what your menu.lst looks like.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
creates results.txt in the same directory, post with code tags as it will be long.

Linux does not need more than one swap although if necessary it will use them.

---

### Post by frilock on 2009-09-30
this is what i got .....:confused:

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
# kopt=root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda5 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda7 
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=d92dd445-b41e-415d-8afd-bf8b6327177a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid= enter 124,devmode=664 0 0





=================== sda7: Location of files loaded by Grub: ===================


  73.0GB: boot/grub/menu.lst
  72.9GB: boot/grub/stage2
  72.9GB: boot/initrd.img-2.6.24-19-generic
  73.1GB: boot/initrd.img-2.6.24-19-generic.bak
  73.0GB: boot/initrd.img-2.6.24-21-generic
  73.0GB: boot/initrd.img-2.6.24-21-generic.bak
  73.0GB: boot/initrd.img-2.6.24-22-generic
  73.0GB: boot/initrd.img-2.6.24-22-generic.bak
  73.0GB: boot/initrd.img-2.6.24-23-generic
  73.0GB: boot/initrd.img-2.6.24-23-generic.bak
  73.0GB: boot/initrd.img-2.6.24-24-generic
  73.1GB: boot/initrd.img-2.6.24-24-generic.bak
  73.0GB: boot/vmlinuz-2.6.24-19-generic
  73.1GB: boot/vmlinuz-2.6.24-21-generic
  73.0GB: boot/vmlinuz-2.6.24-22-generic
  73.0GB: boot/vmlinuz-2.6.24-23-generic
  73.0GB: boot/vmlinuz-2.6.24-24-generic
  73.0GB: initrd.img
  73.0GB: initrd.img.old
  73.0GB: vmlinuz
  73.0GB: vmlinuz.old
```

---

### Post by frilock on 2009-09-30
......................

---

### Post by frilock on 2009-09-30
......................

---

### Post by frilock on 2009-09-30
....................

---

### Post by frilock on 2009-09-30
.........

---

### Post by frilock on 2009-09-30
...................

---

### Post by frilock on 2009-09-30
ok there is all of it can anyone help me out please

---

### Post by frilock on 2009-09-30
bumppp anyone????

---

### Post by oldfred on 2009-10-01
It would have been easier to review if you used the code tags - highlight and click on # in panel above message entry.

You must verify menu.lst is correct and edit fstab to have the correct UUID's

The first line says Ubuntu is in  partition #7
Partition 7 is /dev/sda7: UUID="006d5962-bf4b-454b-ad5b-e039a5dc6adf" SEC_TYPE="ext2" TYPE="ext3"
And in grub sda7 will be (hd0,6)
(the windows in the mbr of the second drive is not useable but is not used so it is ok). Your window in sda1 should boot with the entry in you menu.lst of (hd0,0).

Please correct menu.lst and fstab and see it you can boot or what errors you get. If you still cannot boot rerun the script but please post with the code tags.

In menu.lst your root entry has the smiley over the number so I cannot tell if is a 6 or not. It should be. If it is not, use the live cd to change:

to backup
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
to edit
```
sudo gedit /boot/grub/menu.lst
```
with the live cd you may not need sudo?

Also your fstab says for root entry (UUID is wrong)
# /dev/sda7
UUID=0b942164-5eec-4539-89e5-bb9ee11ddd5c /               ext3    relatime,errors=remount-ro 0       1
but sda7 is the 006d5962-bf4b-454b-ad5b-e039a5dc6adf  This must be changed from the 0b.. to the 006..to have the system boot correctly.
backup
```
sudo cp /etc/fstab /etc/fstab.backup
```
edit
```
sudo gedit /etc/fstab
```

and swap is:
# /dev/sda8
UUID=aff6d2ef-a8ff-4cce-b10a-21b07a647ee4 none            swap    sw              0       0

swap will work but it is on sda9 not sda8, the comment is not critical, but if you delete sda9 & sda10 as extra swaps then you have to also change fstab to have the correct UUID for swap on sda8 to 
d92dd445-b41e-415d-8afd-bf8b6327177a see below for all UUID for swap

but swap could be any of 
/dev/sda8: UUID="d92dd445-b41e-415d-8afd-bf8b6327177a" TYPE="swap" 
/dev/sda9: UUID="aff6d2ef-a8ff-4cce-b10a-21b07a647ee4" TYPE="swap" 
/dev/sda10: UUID="92f4f494-7d46-4c27-b071-5a48e5ed92cb" TYPE="swap" 

The two menu.lst entries at the bottom are strange - the last refering to sda7 looks like it may work? the one refering to sda5 may not work as the install has no menu.lst. The partition sda6 also has an fstab so was it an install?

---

### Post by frilock on 2009-10-01
if the grub is in hd0,6 then why dose it show (hd0,8???
i brought up the menu list but i dont know what to re write 
dose anyone know ??


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
# kopt=root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda5 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda7 
savedefault
boot
```

---

### Post by egalvan on 2009-10-01
Per Forum Rules...

"Bumping" threads is allowed once every 24 hours.

---

### Post by frilock on 2009-10-01
> **oldfred said:**
> The two menu.lst entries at the bottom are strange - the last refering to sda7 looks like it may work? the one refering to sda5 may not work as the install has no menu.lst. The partition sda6 also has an fstab so was it an install?

i had to try to install linux three times i think i cant remember then i found out i had a bad mem stick i replaced it and just installed with out removing the other previous installs i regret it know because its showing partitions i dont even use it was all working fine until i messed with partition magic but what i dont get is why it happened i never finalized anything ...this is so frustrating i really need to get this going if theres no hope im just going to trash this and start over :(

---

### Post by oldfred on 2009-10-01
The easiest way to edit your files is to boot with the live CD.

Use Naulitus/file browser, places, compter, find your filesystem, drill down thru /boot/grub so you can see menu.lst. Do not double click as it will not let you save it but right click, choose open with, in the open with window scroll to the bottom Open with other Application, at bottom where it says use other application, click on it and it will open a single line, type in gksudo gedit and it will open the file in superuser mode so you can save it. It may seem long but is easy once you right click and scroll down.

The other choice is boot from the live CD and use terminal to mount your filesystem, and manually drill down. Lots of typing but we can post that to copy if desired.

Once in menu.lst change all your (hd0,8) to (hd0,6) for ubuntu entries.
save file and then edit the fstab file in /etc. You may want to also open a terminal and type blkid -L so you can copy your UUID's to the fstab rather than trying to type them.

---

### Post by frilock on 2009-10-01
> **oldfred said:**
> The easiest way to edit your files is to boot with the live CD.

Use Naulitus/file browser, places, compter, find your filesystem, drill down thru /boot/grub so you can see menu.lst. Do not double click as it will not let you save it but right click, choose open with, in the open with window scroll to the bottom Open with other Application, at bottom where it says use other application, click on it and it will open a single line, type in gksudo gedit and it will open the file in superuser mode so you can save it. It may seem long but is easy once you right click and scroll down.

The other choice is boot from the live CD and use terminal to mount your filesystem, and manually drill down. Lots of typing but we can post that to copy if desired.

Once in menu.lst change all your (hd0,8) to (hd0,6) for ubuntu entries.
save file and then edit the fstab file in /etc. You may want to also open a terminal and type blkid -L so you can copy your UUID's to the fstab rather than trying to type them.




ok i mannaged to do the first step which was doing this Once in menu.lst change all your (hd0,8) to (hd0,6) for ubuntu entries.
save file now as for editing the fstab how do i do that ???

---

### Post by frilock on 2009-10-01
wit just want to make sure where ever it says (hd0,8 change it to hd0.6 ??
or just change where it says hd0,8 on all these lines ?? 
## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

---

### Post by oldfred on 2009-10-01
all the lines that refer to Ubuntu that say root        (hd0,8) should be (hd0,6) as that is sda7 where Ubuntu is installed.

As I said before:
The first line says Ubuntu is in  partition #7
Partition 7 is /dev/sda7: UUID="006d5962-bf4b-454b-ad5b-e039a5dc6adf" SEC_TYPE="ext2" TYPE="ext3"
And in grub sda7 will be (hd0,6)

As for your fstab, use nautilus and drill down to /etc and open fstab as a super user like you did for menu.lst. You may also want to open a second window and use the  terminal If you 

```
blkid -L
```You will see all your UUID's, you can then copy from the terminal to the fstab entry to correct it to 006d5962-bf4b-454b-ad5b-e039a5dc6adf.

Also your fstab says for root entry (UUID is wrong)
# /dev/sda7
UUID=0b942164-5eec-4539-89e5-bb9ee11ddd5c /               ext3    relatime,errors=remount-ro 0       1
but sda7 is the  This must be changed from the 0b.. to the 006..to have the system boot correctly.
backup

8 - eight is not a smiley

---

### Post by frilock on 2009-10-01
ok i did this part ..As for your fstab, use nautilus and drill down to /etc and open fstab as a super user like you did for menu.lst. 


but i dont understand this parts:confused:

You may also want to open a second window and use the terminal If you

---

### Post by frilock on 2009-10-01
This is what i see in my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=d92dd445-b41e-415d-8afd-bf8b6327177a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid= enter 124,devmode=664 0 0

```

---

### Post by frilock on 2009-10-01
this is what i got when i typed that code into the terminal 


```
ubuntu@ubuntu:~$ blkid -L
blkid: invalid option -- L
blkid 1.0.0 (12-Feb-2003)
usage:  blkid [-c <file>] [-ghl] [-o format] [-s <tag>] [-t <token>]
    [-v] [-w <file>] [dev ...]
        -c      cache file (default: /etc/blkid.tab, /dev/null = none)
        -h      print this usage message and exit
        -g      garbage collect the blkid cache
        -s      show specified tag(s) (default show all tags)
        -t      find device with a specific token (NAME=value pair)
        -l      lookup the the first device with arguments specified by -t
        -v      print version and exit
        -w      write cache to different file (/dev/null = no write)
        dev     specify device(s) to probe (default: all devices)
ubuntu@ubuntu:~$ 

```

---

### Post by oldfred on 2009-10-01
They must have updated blkid in ubuntu 9.10 as it works for me. just do blkid it just is not formated as nice.

This is your fstab entries for root (/) and swap:

# /dev/sda9
UUID=[COLOR=Red]006d5962-bf4b-454b-ad5b-e039a5dc6adf[/COLOR] /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=[COLOR=Red]d92dd445-b41e-415d-8afd-bf8b6327177a [/COLOR]none            swap    sw              0       0[COLOR=Black]

The above fstab looks correct, I thought it was this before:
[/COLOR]0b942164-5eec-4539-89e5-bb9ee11ddd5c which was wrong?

Try booting and see what errors you get.

---

### Post by frilock on 2009-10-01
restarted and i just get disk error now :confused:

---

### Post by oldfred on 2009-10-01
need to know what error - is it a grub number or something further along in Ubuntu?

---

### Post by frilock on 2009-10-01
i cant even get to ubuntu the system starts to boot then it says error disk press any key

---

### Post by frilock on 2009-10-01
ok i used super grub and it said something about error 22 no such partition.  any clue??

---

### Post by oldfred on 2009-10-01
I am lost, I wonder when we edited menu.lst we edited one of your other installls? 
Two choices - back to live cd and rerun the boot info script file. post in code tags (#)
Since you have 3 installs do you have any data in one of them. Totally reinstalling after deleting the 3 current ones and the three current swaps may be quicker?

---

### Post by frilock on 2009-10-01
the only install that im worried about is the one on the 408.4 GB Volume: disk-1  i have a lot of important info on it i just wish i could boot into it and remove what i need then redo it all 
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
# kopt=root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda5 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda7 
savedefault
boot

```

> **oldfred said:**
> I am lost, I wonder when we edited menu.lst we edited one of your other installls? 
Two choices - back to live cd and rerun the boot info script file. post in code tags (#)
Since you have 3 installs do you have any data in one of them. Totally reinstalling after deleting the 3 current ones and the three current swaps may be quicker?

---

### Post by oldfred on 2009-10-01
If you mean the second drive sdb  you can copy data using the liveCD or use Supergrub to reinstall windows boot to your first drive sda. With two 500GB drives you should have room for data and backups. 

Deleting the linux and swap partitions should not cause any problems but we always recommend backing up just in case. Often the system works the way we tell it, its just sometimes we tell it the wrong thing and delete things we do not want to.

---

### Post by frilock on 2009-10-01
is there a way to recover firefox  favorites? 


> **oldfred said:**
> If you mean the second drive sdb  you can copy data using the liveCD or use Supergrub to reinstall windows boot to your first drive sda. With two 500GB drives you should have room for data and backups. 

Deleting the linux and swap partitions should not cause any problems but we always recommend backing up just in case. Often the system works the way we tell it, its just sometimes we tell it the wrong thing and delete things we do not want to.

---

### Post by oldfred on 2009-10-01
If you really want to try some more post the results of the boot info script.
Filefox has a complete profile in a hidden file in your home directory. Using live CD & Naulitus browse to your home directory, Under view check show hidden files. You can copy the entire .mozilla directory all the data is in xxxxxxx.default and profile file tells it where/which xxxxx.default file to use. You should xport the bookmarks to a html file for ease of access. I do it before I backup. If you reinstall you start firefox, close it  and then move the copy inplace of the new xxxx.default. The old profile should point to old default. I believe you can have more than one profile using a profile manager but I just copy profiles from one computer to another when I travel.
Most of you configurations are in hidden files in your home. This is why some suggest a separate partition for /home so when you reinstall all your configurations stay the same.
Using the live CD you should be able to copy the entire home. Look on the interent for move home.
one example
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by frilock on 2009-10-01
here it is info scrip 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef70ef70

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    29,157,974    29,157,912   b W95 FAT32
/dev/sda2          29,157,975   976,768,064   947,610,090   f W95 Ext d (LBA)
/dev/sda5          29,158,038    57,095,009    27,936,972  83 Linux
/dev/sda6          57,095,073    83,827,169    26,732,097  83 Linux
/dev/sda7          83,827,233   940,332,644   856,505,412  83 Linux
/dev/sda8         940,332,708   952,477,784    12,145,077  82 Linux swap / Solaris
/dev/sda9         952,477,848   964,622,924    12,145,077  82 Linux swap / Solaris
/dev/sda10        964,622,988   976,768,064    12,145,077  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 512 MB, 512753664 bytes
16 heads, 32 sectors/track, 1956 cylinders, total 1001472 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbfb8bfb8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     1,001,471     1,001,440   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="10D8-132E" TYPE="vfat" 
/dev/sda5: UUID="5ada9b16-2233-4ca5-b977-5563b912a5b7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="0b942164-5eec-4539-89e5-bb9ee11ddd5c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="006d5962-bf4b-454b-ad5b-e039a5dc6adf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="d92dd445-b41e-415d-8afd-bf8b6327177a" 
/dev/sda9: TYPE="swap" UUID="aff6d2ef-a8ff-4cce-b10a-21b07a647ee4" 
/dev/sda10: TYPE="swap" UUID="92f4f494-7d46-4c27-b071-5a48e5ed92cb" 
/dev/sdb1: UUID="C4C9-1E95" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077,usefree)
/dev/sda7 on /media/disk-1 type ext3 (rw,nosuid,nodev)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\="Microsoft Windows" 


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\="Microsoft Windows" 


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5ada9b16-2233-4ca5-b977-5563b912a5b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=92f4f494-7d46-4c27-b071-5a48e5ed92cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  16.0GB: boot/vmlinuz-2.6.24-19-generic
  16.0GB: vmlinuz

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=0b942164-5eec-4539-89e5-bb9ee11ddd5c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=aff6d2ef-a8ff-4cce-b10a-21b07a647ee4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  29.5GB: boot/vmlinuz-2.6.24-19-generic
  29.5GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda5 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Ubuntu 8.04.1 (8.04) (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/sda7 
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=d92dd445-b41e-415d-8afd-bf8b6327177a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid= enter 124,devmode=664 0 0





=================== sda7: Location of files loaded by Grub: ===================


  73.0GB: boot/grub/menu.lst
  72.9GB: boot/grub/stage2
  72.9GB: boot/initrd.img-2.6.24-19-generic
  73.1GB: boot/initrd.img-2.6.24-19-generic.bak
  73.0GB: boot/initrd.img-2.6.24-21-generic
  73.0GB: boot/initrd.img-2.6.24-21-generic.bak
  73.0GB: boot/initrd.img-2.6.24-22-generic
  73.0GB: boot/initrd.img-2.6.24-22-generic.bak
  73.0GB: boot/initrd.img-2.6.24-23-generic
  73.0GB: boot/initrd.img-2.6.24-23-generic.bak
  73.0GB: boot/initrd.img-2.6.24-24-generic
  73.1GB: boot/initrd.img-2.6.24-24-generic.bak
  73.0GB: boot/vmlinuz-2.6.24-19-generic
  73.1GB: boot/vmlinuz-2.6.24-21-generic
  73.0GB: boot/vmlinuz-2.6.24-22-generic
  73.0GB: boot/vmlinuz-2.6.24-23-generic
  73.0GB: boot/vmlinuz-2.6.24-24-generic
  73.0GB: initrd.img
  73.0GB: initrd.img.old
  73.0GB: vmlinuz
  73.0GB: vmlinuz.old
```

---

### Post by oldfred on 2009-10-01
Everything I look at looks correct. The only question I have is in the windows you have double entries with one lowercase and one in CAPS.
/boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

The liveCD allows a boot from the first HD. I do not know if that is any different than a normal boot. [COLOR=DarkRed]You do have sda booting first in BIOS? [/COLOR]The second drive sdb will not boot as a windows entry is there in the MBR but not correct.

Highlights that I look at to match  and they do, except for the comments in fstab for sda7 which should not prevent booting.

Grub0.97 is installed in the MBR of /dev/sda
looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst
sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

/dev/sda7: UUID="006d5962-bf4b-454b-ad5b-e039a5dc6adf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="d92dd445-b41e-415d-8afd-bf8b6327177a"


title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

# /dev/sda[COLOR=DarkRed]9[/COLOR] [COLOR=Red]uuid is for 7 and 7 is correct[/COLOR]
UUID=006d5962-bf4b-454b-ad5b-e039a5dc6adf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda[COLOR=DarkRed]10[/COLOR] [COLOR=Red]uuid is for 8 and 8 is ok (any of 3 swaps will work)[/COLOR]
UUID=d92dd445-b41e-415d-8afd-bf8b6327177a none            swap    sw  

Comments do not match but UUIDs  do match to the partitions you are using.

---

