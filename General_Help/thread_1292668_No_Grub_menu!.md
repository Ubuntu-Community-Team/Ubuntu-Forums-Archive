---
title: "No Grub menu!?"
date: 2009-10-16
forum: General Help
---

### Post by webaake on 2009-10-16
Firstly, I don't do dual boot and the system boots fine. I just don't see the grub menu, never have from Feisty thru Jaunty. hiddenmnu is of course commented out (##hiddenmenu), timeout is set to 10.

Today I found some new parameters to test after the ##hiddenmenu line in menu.lst;
# Hides the menu by default (press ESC to see the menu)
##hiddenmenu
console=tty0 video=vesafb vga=0x31

tried console=tty1 as well
tried console=tty1 at the kernel line as well, no luck.

I've tried grub2 - no luck.

One big problem is that when you google for "no grub menu" you get a LOT of dual boot problems. So far I've found no one with the same problems as me - I can't see the grub menu! I know it's there because timeout works, and pressing Esc works, and then pressing Enter works to boot the first kernel option. I just don't see it!

---

### Post by zzzBrett on 2009-10-16
> **webaake said:**
> Firstly, I don't do dual boot and the system boots fine. I just don't see the grub menu, never have from Feisty thru Jaunty. hiddenmnu is of course commented out (##hiddenmenu), timeout is set to 10.

Today I found some new parameters to test after the ##hiddenmenu line in menu.lst;
# Hides the menu by default (press ESC to see the menu)
##hiddenmenu
console=tty0 video=vesafb vga=0x31

tried console=tty1 as well
tried console=tty1 at the kernel line as well, no luck.

I've tried grub2 - no luck.

One big problem is that when you google for "no grub menu" you get a LOT of dual boot problems. So far I've found no one with the same problems as me - I can't see the grub menu! I know it's there because timeout works, and pressing Esc works, and then pressing Enter works to boot the first kernel option. I just don't see it!


When the menu is hidden, I think you can press the escape button to see it.  If you can't get to the menu, seems like you could remove grub and 'reinstall' it from the beginning.

---

### Post by webaake on 2009-10-16
Reinstall doesn't solve it - as I've explained the menu IS there. It just isn't viewable on screen.

---

### Post by Kevbert on 2009-10-16
Please post your menu.lst file.

---

### Post by webaake on 2009-10-16
Here it is:
cat /boot/grub/menu.lst
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
default         saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
##hiddenmenu
##EGET TEST:
##console=tty0 video=vesafb vga=0x311
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
# kopt=root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89

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
# defoptions=video=vesafb vga=0x311

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
# howmany=4

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##

title           Kernel 2.6.31-new
uuid            afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel          /boot/vmlinuz-2.6.31-new root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 resume=UUID=c146d320-599e-4f9a-bae5-3922ef3c9514 ro console=tty1 video=vesafb vga=0x311
initrd          /boot/initrd.img-2.6.31-new
savedefault

title           Kernel 2.6.30-new
uuid            afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel          /boot/vmlinuz-2.6.30-new root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 resume=UUID=c146d320-599e-4f9a-bae5-3922ef3c9514 ro video=vesafb vga=0x311
initrd          /boot/initrd.img-2.6.30-new
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.29.3
uuid		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/vmlinuz-2.6.29.3 root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 ro video=vesafb vga=0x311  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.29.3
quiet
savedefault

title		Ubuntu 9.04, kernel 2.6.29.3 (recovery mode)
uuid		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/vmlinuz-2.6.29.3 root=UUID=afabfa9a-c18d-42e1-bfc3-bc087cdd9b89 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.29.3

title		Chainload into GRUB 2
root		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/grub/core.img
savedefault

title		Ubuntu 9.04, memtest86+
uuid		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Niko Johnson on 2009-10-16
whats up with this line

 title		Chainload into GRUB 2
root		afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel		/boot/grub/core.img
savedefault

is that suppose to be there? try commenting that out and rebooting.

---

### Post by Kevbert on 2009-10-16
You've also set 
```
timeout 0
```
try setting it to say 10 seconds.
With
```
default saved
```
I'm assuming that you are trying to boot the kernel that you last ran (either Karmic or Jaunty).

---

### Post by webaake on 2009-10-16
Sry, posted my present menu.lst in use. Of course I've tried all sorts of timeouts.

I have no problem booting, that's not it. This problem has persisted on all kernels from Feisty thru Jaunty, standard and self compiled; no viewable grub menu.

---

### Post by P4man on 2009-10-16
Grub is probably using a resolution/color depth your monitor can't handle. You could try installing startup-manager and trying various resolutions / color depths. You can do that by editing grub config files as well, if you find a table somewhere with the required codes.

---

### Post by webaake on 2009-10-16
This video=vesafb vga=0x311 at the end of the kernel line fixes resolution for the boot up. But as far as I understand it, this is after the grub menu should be displayed.

Startupmanager also edits what is happening after grub menu and up until login.

So, if there's a way to direct grub at initial boot to the right tty with the right resolution I think it would be OK. If I only knew how?

---

### Post by P4man on 2009-10-16
you can change both grub and usplash settings in startupmanager afaik. At least for grub2.

Anyway, for grub2:
[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

For legacy grub, Im not sure how (or if its even possible).

---

### Post by lavinog on 2009-10-16
is it possible you are using grub2...in which case i don't think menu.lst is used

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2):
> While the main grub bootloader file continues to reside in the /boot/grub folder, it is no longer Grub's familiar menu.lst. The main Grub 2 instruction file is now grub.cfg. This file is produced by various scripts run when either the "update-grub" or "update-grub2" command is executed. The files primarily responsible for the content of grub.cfg are /etc/default/grub and individual script files located in /etc/grub.d/

---

### Post by webaake on 2009-10-16
Nope.

---

### Post by lavinog on 2009-10-16
Then why do you have this line?
```

title Chainload into GRUB 2
root afabfa9a-c18d-42e1-bfc3-bc087cdd9b89
kernel /boot/grub/core.img
savedefault

```

---

### Post by webaake on 2009-10-16
That's a remmnant from a forner grub 2 test install. I'm sure it doesn't matter since I'm booting from the first kernel line.

---

### Post by lavinog on 2009-10-16
So you installed grub2 at some point.
How did you uninstall it?

How do you know you are booting from the first kernel line...you have "default saved" set

what does /boot/grub/default say the saved default is?

also what does this say:
```

uname -a

```

I wonder if reinstalling grub would work.

---

### Post by webaake on 2009-10-16
sudo cat /boot/grub/default
[sudo] password for mrmedia: 
0







#
#
#
#
#
#
# WARNING: If you want to edit this file directly, do not remove any line
# from this file, including this warning. Using `grub-set-default\' is
# strongly recommended.
mrmedia@mediamaskinen:~$ sudo cat /boot/grub/default
0







#
#
#
#
#
#
# WARNING: If you want to edit this file directly, do not remove any line
# from this file, including this warning. Using `grub-set-default\' is
# strongly recommended.

---

### Post by webaake on 2009-10-17
I'm booting kernel 2.6.31-new.

---

