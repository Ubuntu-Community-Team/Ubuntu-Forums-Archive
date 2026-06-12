---
title: "Can't load vista from grub!"
date: 2009-10-17
forum: General Help
---

### Post by mjpeez on 2009-10-17
Alright I am about to lose my mind... I know others have had this problem, but I can't seem to get it resolved.

I am trying to dual boot ubuntu jaunty with vista...

I have followed all of the online tutorials on how to set up your grub... it will not work

when i select vista in the bootloader, i get "Try (hd0,0): EXT2: _" on a blank black screen... i have let it sit for minutes.... NOTHING!

here is my fdisk -l output::::

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50495049

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2155    17310006   83  Linux
/dev/sda2   *        2156        4310    17308672    7  HPFS/NTFS
/dev/sda3            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe60693fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601    7  HPFS/NTFS





ok now here is my menu.lst::::

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=1f336e96-5d92-4124-a4d2-e038eed98a49 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1f336e96-5d92-4124-a4d2-e038eed98a49

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        1f336e96-5d92-4124-a4d2-e038eed98a49
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1f336e96-5d92-4124-a4d2-e038eed98a49 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        1f336e96-5d92-4124-a4d2-e038eed98a49
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1f336e96-5d92-4124-a4d2-e038eed98a49 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        1f336e96-5d92-4124-a4d2-e038eed98a49
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=1f336e96-5d92-4124-a4d2-e038eed98a49 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        1f336e96-5d92-4124-a4d2-e038eed98a49
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=1f336e96-5d92-4124-a4d2-e038eed98a49 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1f336e96-5d92-4124-a4d2-e038eed98a49
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1f336e96-5d92-4124-a4d2-e038eed98a49 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1f336e96-5d92-4124-a4d2-e038eed98a49
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1f336e96-5d92-4124-a4d2-e038eed98a49 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1f336e96-5d92-4124-a4d2-e038eed98a49
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title    Windows Vista
root    (hd0,1)
makeactive
chainloader +1






WHAT AM I DOING WRONG HERE???? IS IT SOME KIND OF HARDWARE ISSUE????
The HDD is a western digital raptor....... i don't think i am running raid on it... it's sata though.

---

### Post by beastrace91 on 2009-10-18
Try editing this ```
title Windows Vista
root (hd0,1)
makeactive
chainloader +1
```

To look like this: ```
title Windows Vista
root (hd0,2)
makeactive
chainloader +1
```

Regards,
~Jeff

---

### Post by xxterry1xx on 2009-10-18
well i cant put my menu.lst config because its gonna get cluttered so you have some unneeded kernels in there use ubuntu-tweak to get rid of if your not using them     ### END DEBIAN AUTOMAGIC KERNELS LIST  # This is a divider, added to separate the menu items below from the Debian # ones. title Other operating systems: root   # This entry automatically added by the Debian installer for a non-linux os # on /dev/sda1 title Windows Vista (loader) rootnoverify (hd0,0) savedefault makeactive chainloader +1

---

### Post by carnagex420x on 2009-10-18
Vista is actually # on /dev/sda2.
try:
title Vista
root (hd0,1)
chainloader +1

But make sda1 (your linux partition) active instead, while removing makeactive from vista.

---

### Post by jayanramesh on 2009-10-18
Dear mjpeez

Download "super grub disk" and burn iso file on your cd with your favourite burning software k3b or brasero. It will take care of your problem.> [http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso]("http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso")

---

### Post by beastrace91 on 2009-10-18
> **carnagex420x said:**
> 
try:
title Vista
root (hd0,1)
chainloader +1

Did you read his post? Thats what he has now...

~Jeff

---

### Post by oldfred on 2009-10-18
try rootnoverify and makeactive is not required if the * or boot is set for the windows partition. Linux does not need the boot flag.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1

---

### Post by carnagex420x on 2009-10-18
> **beastrace91 said:**
> Did you read his post? Thats what he has now...

~Jeff

Did you read mine?

-But make sda1 (your linux partition) active instead, while removing makeactive from vista.

That was my big idea... also adding rootnoverify sounds like a good idea too.

---

