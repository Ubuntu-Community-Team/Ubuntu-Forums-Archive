---
title: "How to install new distro along with ubuntu and windows"
date: 2009-07-05
forum: General Help
---

### Post by sundar_ima on 2009-07-05
I have five partition in my laptop. Installed Winxp and Ubuntu (default) on different partitions. Now planning to test different distro on the third partition. My question is that how can i install new distro with out changing ubuntu and windows setup? and I want to keep ubuntu as my default boot option.

Earlier i have tried opensuse but after installation ubuntu vanished from the boot option.

---

### Post by ivanvajar on 2009-07-05
I have no experience with openSuse, but you should be able to install system without installing BootLoader. Later, just add entries for new system to egzisting menu.lst

---

### Post by ShadowWraith on 2009-07-05
I have Windows, Ubuntu, and Fedora all running on my machine. I installed Ubuntu last. It automatically detected windows (I think all installers can do that) but it ignored Fedora. Luckily, the problem wasn't too hard to fix.

Both Ubuntu and Fedora had their own versions of /boot/grub/menu.lst . To make the old Fedora option be the default, I mounted the fedora partition in ubuntu, and opened /etc/boot/menu.lst . There, I just cut and pasted the Fedora boot option to my new default menu.lst in Ubuntu's /boot/grub/menu.lst .

You should be able to do this too, depending on what distro you intend to install.


As an example, here is my menu.lst
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
# kopt=root=UUID=ad0e26f7-40f8-440a-8dcd-e5cea1977fb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ad0e26f7-40f8-440a-8dcd-e5cea1977fb3

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
title Fedora (2.6.27.21-78.2.41.fc9.i686)
        root (hd1,0)
        kernel /vmlinuz-2.6.27.21-78.2.41.fc9.i686 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.27.21-78.2.41.fc9.i686.img

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		ad0e26f7-40f8-440a-8dcd-e5cea1977fb3
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ad0e26f7-40f8-440a-8dcd-e5cea1977fb3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		ad0e26f7-40f8-440a-8dcd-e5cea1977fb3
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=ad0e26f7-40f8-440a-8dcd-e5cea1977fb3 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ad0e26f7-40f8-440a-8dcd-e5cea1977fb3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ad0e26f7-40f8-440a-8dcd-e5cea1977fb3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ad0e26f7-40f8-440a-8dcd-e5cea1977fb3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ad0e26f7-40f8-440a-8dcd-e5cea1977fb3 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ad0e26f7-40f8-440a-8dcd-e5cea1977fb3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```


Each paragraph that doesn't start with a # (that means it's commented out) and starting with "title" is another menu entry. Since menu.lst is standardized, you can cut and paste any distro's entry to another distro's menu.lst .

(warning: make sure you know how to mount other partitions in the command line before you try this, since not all distro's will mount all of the other partitions on the drive manually)

Good luck!

---

### Post by sundar_ima on 2009-07-06
Thanks for your reply guys...

> you should be able to install system without installing BootLoader 

how to do that???

@ ShadowWraith
I have tried this in my USB pendrive with multiple Linux OS. Let me try in hard disk...

---

### Post by loomsen on 2009-07-06
You may, and you should choose where to install the bootloader to in almost every distros installer.

Either don't install any bootloader at all and adjust your grub menu to boot the kernels, or install the distros native bootloader to the root partition rather than the MBR. 

The MBR is the first sector of your harddrive, so it won't have a partition number.
Grub annotation:
(hd0)

which equals

/dev/sda

So, alter the location to install the bootloader to during installation to be 

/dev/sda7 
for instance if your suse root is on sda7.

NOTE: in grub annotation this would be
(hd0,6)

If you choose to go without any bootloader install, your grub menu should look like:
[color=red]NOTE: kernel and initrd located in <partition>/boot/vmlinuz [/color]
```

title bluewhite64
root (hd0,7)  ## <-- setting the root partition
kernel /boot/vmlinuz root=LABEL=bw64 acpi_osi="Linux" vga=791 quiet
initrd /boot/initrd

```

If you choose to install to your root partition, your entry to your existing grub would be

```

title bluewhite64
rootnoverify (hd0,6)
chainloader +1

```

This will switch to the specified partition and launch the bootloader installed onto the partitions first sector.

For my USB to boot from my current grub I use:
[color=red]NOTE: my USB stick holds the links to the kernel and the initrd in <stick>/ as opposed to bluewhite above where these are in /boot/[/color]
```

title debian USB
	root (hd1,0)
	kernel	(hd1,0)/vmlinuz ro root=LABEL=usb acpi_osi="Linux" vga=791 quiet
	initrd	(hd1,0)/initrd.img

```

which is a bootstrapped debian system I pulled in inside a chroot. So not even an installation is required...
Just need to make sure grub recognizes the stick as well, so 
/boot/grub/device.map

has to include the proper information for grub. This is

```

(hd0)	/dev/sda
(hd1) /dev/sdb   ##<-- added this to boot from USB without choosing USB boot from my BIOS menu
```

Additional notes you might want to know as well:
The first specification of 
root (hdX,Y)
changes to the drive containing your kernel (vmlinuz), checking it in ro, initializing your CPU, pci devices etc, then the second
root=LABEL or root=/dev/sdXY or root=UUID  ## NOTE: use the LABEL option for ease of use, just add LABELs to all your partitions.
changes the root partition to <specified> and remounts your kernel rw and finally boots up your system using the order and modules specified inside the
initrd.img
it is pointed to.

This is my whole grub.conf, including all different options
```

# grub.conf generated by anaconda
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/sda7
#          initrd /initrd-version.img
############## test #############
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
#hiddenmenu
title Fedora (2.6.29.6)
	root (hd0,0)
	kernel /vmlinuz ro root=LABEL=fedora acpi_osi="Linux" vga=791 quiet
	initrd /initrd
title bluewhite64
	root (hd0,7)
	kernel /boot/vmlinuz root=LABEL=bw64 acpi_osi="Linux" vga=791 quiet
	initrd /boot/initrd
title sidux
	rootnoverify (hd0,8)
	chainloader +1
title debian USB
	root (hd1,0)
	kernel	(hd1,0)/vmlinuz ro root=LABEL=usb acpi_osi="Linux" vga=791 quiet
	initrd	(hd1,0)/initrd.img

```

---

### Post by sundar_ima on 2009-07-06
@ loomsen 

excellent tutorial. thank you very much man :p

---

### Post by sundar_ima on 2009-08-07
After starting this thread i have installed Mandriva 2009.1 and it worked flawlessly during boot up. It also detected all my OS. Today i have installed Ubuntu's sister "Linus Mint 7 Kde". It booted my system but on the boot screen there is only one enty for linux mint i.e. "Linux Mint 7 Gloria KDE, memtest86+" and no option to boot Linux Mint. There is no issue with rest of the OS (ubuntu and Win). Here is the menu.lst file content of the linux mint (which i have installed in /dev/sda7)

```

## ## End Default Options ##

title		Linux Mint 7 Gloria KDE, memtest86+
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda9.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=782b725c-adf6-4bbb-9c14-2b19ed888f50 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda9.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda9)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=782b725c-adf6-4bbb-9c14-2b19ed888f50 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda9.
title		Ubuntu 9.04, memtest86+ (on /dev/sda9)
root		(hd0,8)
kernel		/boot/memtest86+.bin  
savedefault
boot
```

and i modified the mint entry like this 

```

title		Linux Mint 7
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=782b725c-adf6-4bbb-9c14-2b19ed888f50 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot

```

Up on reboot it gave me "error 15" " file not found". So I checked for the files vmlinuz and intrd.img. There was no vmlinuz file in /boot/. So copied one from the extracted iso file of linux mint 7 kde.

Again rebooted with all the modification. It booted well and i could see the linux mint boot screen but finally landed in Ubuntu 9.04. Previously I installed Kubuntu 9.04 on this same drive and I had no issues with it. 

Any help would be appreciated.

Sundar

---

### Post by sundar_ima on 2009-08-09
I got it done. This is the problem with UUID value. I had to change the UUID value with "/dev/sda7".

---

