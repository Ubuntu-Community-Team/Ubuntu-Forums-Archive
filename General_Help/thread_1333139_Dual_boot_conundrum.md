---
title: "Dual boot conundrum"
date: 2009-11-21
forum: General Help
---

### Post by qepsilonp on 2009-11-21
my XP hard disk is currently meeting its maker as it has 168 bad sectors and growing so i need to remove XP from my boot screen and remove the drive how would i go about doing this without getting an error message?

also I have bought a spanking new 1TB drive and windows 7 when i install it will it automatically be added to the boot screen?

PS thank god my ubuntu install is on another drive :D

---

### Post by prshah on 2009-11-21
> **qepsilonp said:**
> i need to remove XP from my boot screen and remove the drive how would i go about doing this without getting an error message?

new 1TB drive and windows 7 when i install it will it automatically be added to the boot screen?

my ubuntu install is on another drive

You will have to post some more information for these questions to be answered accurately.

a) Please boot into Ubuntu, open a terminal (Applications-Accessories-Terminal) and post back the output to the following commands```
sudo fdisk -l
cat /boot/grub/menu.lst
``` This will tell us something about the structure of your disks and current installation.

b) When you remove the XP hard disk, you might lose the ability to boot into Ubuntu; this is because the booting program (called "GRUB") may be installed in the XP drive's MBR (Master Boot Record); the above commands will indicate if this problem exists.

c) When you install Windows 7, you will lose the ability to boot into Ubuntu. Your files and data on the Ubuntu drive will remain safe, but you will not get the "GRUB" screen that will allow you to select Ubuntu.

d) In both cases, the fix is fairly easy, and requires a re-installation of GRUB that can be performed from either a live CD or a dedicated GRUB install CD.

e) The order of the drives may change in the BIOS, and may need to be set right. This can be done after Win7 installation, if the need arises.


Please post back with the requested information for more specific instructions.

---

### Post by lmarmisa on 2009-11-21
Maybe you can remove  the ill XP disk from your system and connect your Ubuntu disk in its place (SATA or IDE interface). So, after of that operation, the Ubuntu disk will be connected to the most prioritary disk interface. Its new location will be /dev/sda (or hd0 for grub).

The next step will be install the grub loader in your Ubuntu disk. Start your system with a Live CD Ubuntu, open a terminal and type:

[B]sudo bash
fdisk -l[/B]

Take note of the Linux Ubuntu partition. I will suposse /dev/sda1 (change it if neccesary)

[B]mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda #no mumber here; only sda
[/B]
Then the grub config file (grub: **/boot/grub/menu.lst**; grub2: **/boot/grub/grub.cfg**) will be updated with this command

**update-grub**

Shutdown, remove the Live CD and restart. That is all.

Try to connect the new disk (and install there Windows 7 if you wish) after this change in your system.

Best regards,

Luis

---

### Post by qepsilonp on 2009-11-21
*b) When you remove the XP hard disk, you might lose the ability to boot into Ubuntu; this is because the booting program (called "GRUB") may be installed in the XP drive's MBR (Master Boot Record); the above commands will indicate if this problem exists.*

Ha that makes scene i removed the drive and tried to boot and it said GRUB error now every time i try and boot it says GRUB loading pleas wait then error 22 or something like that and i cant boot so then i have to go into the BOIS boot screen and load up the first drive the XP drive tbh i need to transfer the GRUB to the linux disk now because as i said the XP drive is likely to fail sooner rather than later 

also i dont get my Windows 7 disk tell Wednesday so i need to get the GRUB over to the linux drive before the XP drive fails and i am unable to boot at all.

```
 epsilon@AlphaDesktop:~$ sudo fdisk -l
[sudo] password for epsilon: 

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c8bcfba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         764     6136798+  12  Compaq diagnostics
/dev/sda2   *         765       10079    74822737+   7  HPFS/NTFS
/dev/sda3           10080       19457    75328785    c  W95 FAT32 (LBA)

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009da4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38162   306536233+  83  Linux
/dev/sdb2           38163       38913     6032407+   5  Extended
/dev/sdb5           38163       38913     6032376   82  Linux swap / Solaris 
``````


epsilon@AlphaDesktop:~$ cat /boot/grub/menu.lst
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=a2e98373-5e17-4dc5-8f93-9223f703ff1a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a2e98373-5e17-4dc5-8f93-9223f703ff1a

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
# defoptions=quiet splash vga=792

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
# howmany=1

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        a2e98373-5e17-4dc5-8f93-9223f703ff1a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=a2e98373-5e17-4dc5-8f93-9223f703ff1a ro quiet splash vga=792 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        a2e98373-5e17-4dc5-8f93-9223f703ff1a
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=a2e98373-5e17-4dc5-8f93-9223f703ff1a ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        a2e98373-5e17-4dc5-8f93-9223f703ff1a
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

---

### Post by qepsilonp on 2009-11-21
[I]Maybe you can remove the ill XP disk from your system and connect your Ubuntu disk in its place (SATA or IDE interface). So, after of that operation, the Ubuntu disk will be connected to the most prioritary disk interface. Its new location will be /dev/sda (or hd0 for grub).

The next step will be install the grub loader in your Ubuntu disk. Start your system with a Live CD Ubuntu, open a terminal and type:

[B]sudo bash
fdisk -l[/B]

Take note of the Linux Ubuntu partition. I will suposse /dev/sda1 (change it if neccesary)

[B]mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda #no mumber here; only sda
[/B][/I]      

Having a problem with the [B]grub-install /dev/sda
[/B]it said

```
 root@ubuntu:/# grub-install /dev/sda
/dev/sdb1: Not found or not a block device. 
```

---

