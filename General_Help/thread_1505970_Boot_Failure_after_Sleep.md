---
title: "Boot Failure after Sleep"
date: 2010-06-09
forum: General Help
---

### Post by Chaconne on 2010-06-09
Hello, all,

I encountered a serious problem of boot failure in my Lucid system. It was after the sleep and the machine became not accessible when I pressed the power button. Then I gave it a full power up and it can not boot. The error message is the following
```
Disk Boot Failure, Insert System Disk and Press Enter
```

Fortunately I still have a Hardy Live CD and I booted from that CD. I tried to recover the MBR with the following command
```
sudo grub
find /boot/grub/stage1
root (hd0,2) # My boot partition is sda3
setup (hd0,2)
quit
```
However, it dos not help.

BTW, I'm still using the old grub although my system is Lucid. OTOH, I can boot into the system if I first boot with Live CD and select **boot from the first harddisk** in the menu. Another thing that I'd like to mention is I have to set CD as higher boot priority than harddisk in my BIOS, otherwise it will still attempt to boot from harddisk and display the error message. The reason I guess is BIOS actually thinks the harddisk is bootable.

My final activity before I sleep last night was upgrading software(I found over 100M to upgrade so I left the computer running). I still had MLdonkey and JDownloader runing at that time. My power management setting was to go to sleep after 2 hours of inactivity and spin down the harddisk when possible-- It seems to me a very dangerous option now. The machine has been gone into sleep and successfully waked up for a few times before with the same power management setting.

Any comments are highly appreciated! Thanks in advance.

---

### Post by Chaconne on 2010-06-09
Here is my menu.lst at the moment. I have only one OS(Lucid) on this hard disk. I have 2 hard disk in the system and the other hard disk does not have OS installed, though it's partitioned in ext3.

Since I can still boot into the hard disk with the aid of a Live CD, I think I can rule out the possibility of SATA cable connection problem.

Thanks in advance for any helpful comments.

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
timeout		4

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=ac40132a-8eb9-4831-9a6d-8e79f7c24cdd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# howmany=2

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=ac40132a-8eb9-4831-9a6d-8e79f7c24cdd ro quiet splash
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=ac40132a-8eb9-4831-9a6d-8e79f7c24cdd ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ac40132a-8eb9-4831-9a6d-8e79f7c24cdd ro quiet splash nomodeset
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=ac40132a-8eb9-4831-9a6d-8e79f7c24cdd ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Chaconne on 2010-06-10
I think I found the cause of the problem. Since I have 2 hard disks, it seems my BIOS mistakenly chose the one without OS as boot disk and it did not look further to the other disk. After I change the boot priority between the 2 hard disks in BIOS setting, I can boot from hard disk again. However what triggered BIOS to alter the boot priority of the 2 hard disks is still a mystery.

---

