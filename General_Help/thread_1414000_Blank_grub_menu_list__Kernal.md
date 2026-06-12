---
title: "Blank grub menu list ? Kernal"
date: 2010-02-23
forum: General Help
---

### Post by coolclassic on 2010-02-23
On starting, computer boots to grub but grub fails to show menu list. The list is there as pressing on enter the computer continues to boot to log in screen, unfortunately the screen/monitor is now unstable and goes blank after a few seconds. I now need to reboot computer to try and get to menu list for a stable system. The problem is intermittent.

I wonder is this a problem within the kernal? as I can't think of anything within grub that could affect the monitor.

(I had a similar problem before when the screensaver kicked in.  When left for a period of time the screen/monitor would not restart, fixed that problem within xorg.conf).

---

### Post by plucky on 2010-02-23
> **coolclassic said:**
> On starting, computer boots to grub but grub fails to show menu list. The list is there as pressing on enter the computer continues to boot to log in screen, unfortunately the screen/monitor is now unstable and goes blank after a few seconds. I now need to reboot computer to try and get to menu list for a stable system. The problem is intermittent.

I wonder is this a problem within the kernal? as I can't think of anything within grub that could affect the monitor.

(I had a similar problem before when the screensaver kicked in.  When left for a period of time the screen/monitor would not restart, fixed that problem within xorg.conf).


What version of Kubuntu are you running? Karmic 9.10,Jaunty 9.04,Hardy 8.04

---

### Post by coolclassic on 2010-02-23
Karmic 9.10

---

### Post by plucky on 2010-02-23
Are you dual booting or is Kubuntu the only operating system?


From [here](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

> 
# GRUB_HIDDEN_TIMEOUT=0

    * The hidden timeout option allows a screen to be displayed without the Grub 2 menu, awaiting input from the user for a given number of seconds. It is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
      On single-OS computers:
          o The menu will be hidden unless the user adds a # symbol to the beginning of this line ( # GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
          o If a background image is designated in 05_debian_theme it will be displayed rather than a blank screen during a hidden menu timeout.
          o For integers greater than 0:
                + The system will pause without displaying a menu for the designated number of seconds. If the user does not press the SHIFT key during the timeout the system will then boot the default OS/kernel.
                + If the user presses the SHIFT key to display the menu, the menu will be displayed for the number of seconds designated by the GRUB_TIMEOUT value unless the user again intervenes.
          o With a value of 0:
                + Unless the user intervenes, the system will boot the default OS/kernel with only a slight delay. No menu will be displayed.
                + The user may force displaying the menu as the computer boots by holding down the SHIFT key.


If the grub menu doesn't show up then it is probably what is quoted above.
Also the setup for the monitor can cause nothing to be displayed on startup.
The parameter **gfxpayload** can be used to set the resolution of the display to one that will display at startup.


Good Luck

---

### Post by coolclassic on 2010-02-24
Here is my grub menu as you can see time out is set to 10. As stated in my first post this is an intermittent error and does not occur at every boot. On some occasions the boot process shoots pass grub menu list on every boot (10+ reboots) before getting a menu list. Without the menu list I can not login to kubuntu. Login screen only shoes for seconds before disappearing to a black screen.

-------------------------------------------------------------

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
# kopt=root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49d8de4d-dafc-44a6-bbf4-bccb3e07678f

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=49d8de4d-dafc-44a6-bbf4-bccb3e07678f ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		49d8de4d-dafc-44a6-bbf4-bccb3e07678f
kernel		/boot/memtest86+.bin
quiet

---

