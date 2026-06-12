---
title: "Dual-booting problem...  I need advice"
date: 2009-08-14
forum: General Help
---

### Post by ensleepent on 2009-08-14
I installed Ubuntu 9.04 dual-boot style on a machine that already had Windows XP to see if I liked it.  I did (and do).  So I installed it on another machine that had Windows XP on it, did everything like I did before.  Ubuntu works fine...  but Windows XP now fails to boot on this computer.  I don't know why.  It boots fine on the other one.

Grub seems okay, but when I select Windows XP, I immediately get this:

TRAP 00000006 =====EXCEPTION=======

tr=0028  cr0=80000011  cr2=00F0560B  cr3=00039000
gdt limit=03FF  base=0003F000    idt limit=07FF  base=0003F400

cs:eip=0008:0040737F  ss:esp=0010:0005F95C  errcode=0000
flags=00010086  NoCy NoZr IntDis Down TrapDis
eax=00008000  ebx=00008000  ecx=00000000  edx=00480001 ds=0010  es=0010
edi=80507580  esi=00488000  ebp=0005F978  cr0=80000011 fs=0030  gs=0000

(It's too bad I couldn't copy and paste that...  I hope I didn't make any typos.)  I have no idea what any of this means.  It's gibberish to me.  Maybe somebody here speaks this strange language.

For the record, I did defragment everything before I shrunk XP's partition to make room and installed Ubuntu.  And I don't have a Windows XP disc (my computers came with it installed and no CD).  Any idea where I can get one, by the way?  Or download a good ISO I can use?  I might need that...

Anyway, here's what "sudo fdisk -l" gets me:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93e793e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         966        5347    35198415    7  HPFS/NTFS
/dev/sda2               1         965     7751331    b  W95 FAT32
/dev/sda3            5470        9729    34218450   83  Linux
/dev/sda4            5348        5469      979965    5  Extended
/dev/sda5            5348        5469      979933+  82  Linux swap / Solaris

Partition table entries are not in disk order
ensleepent@ensleepent-desktop:~$ 


And here's what "gksudo gedit /boot/grub/menu.lst" gets me:

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
timeout        10

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
# kopt=root=UUID=ad00563d-95c8-4774-9698-77e2cf855742 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ad00563d-95c8-4774-9698-77e2cf855742

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ad00563d-95c8-4774-9698-77e2cf855742
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ad00563d-95c8-4774-9698-77e2cf855742 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ad00563d-95c8-4774-9698-77e2cf855742
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ad00563d-95c8-4774-9698-77e2cf855742 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ad00563d-95c8-4774-9698-77e2cf855742
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows NT/2000/XP
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


So!  Any thoughts on what my problem might be?  I'm out of ideas.

And while I'm here...  why is it that my Ubuntu won't let me set the screen resolution any higher than 800x600?  And it says I'm using an "unknown monitor."  It's just some Acer flatscreen thing, always plugged-and-played for me before.

---

