---
title: "Grub doesn't seem to notice menu.lst after recovering from Windows Install"
date: 2009-11-20
forum: General Help
---

### Post by Gorf on 2009-11-20
Greetings all, after throwing Winblows 7 onto a small area of extra space on my hard drive, I recovered the Grub install just like:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

And it worked great except there was no menu.  A quick update via "sudo update-grub" fixed that, however now Grub doesn't seem to even detect the menu.lst file that update-grub created in /boot/grub.  So I am stumped.  I can't even hit ESC fast enough to try to get into the grub shell at boot, it just immediately loads Ubuntu 9.10.  I've made sure that the menu.lst file has the hiddenmenu disabled by commenting it out and I increased the wait time on the menu to like 10 seconds.

Can anyone offer opinions or advice on how to correct this?

Here is my menu.lst file:

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
# hiddenmenu

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
# kopt=root=UUID=a724b9d5-40a3-4408-850d-5b99f4b09c7c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=99550239-9eb2-425f-915c-91aaebcc129b

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		99550239-9eb2-425f-915c-91aaebcc129b
kernel		/vmlinuz-2.6.31-15-generic root=UUID=a724b9d5-40a3-4408-850d-5b99f4b09c7c ro quiet splash 
initrd		/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		99550239-9eb2-425f-915c-91aaebcc129b
kernel		/vmlinuz-2.6.31-15-generic root=UUID=a724b9d5-40a3-4408-850d-5b99f4b09c7c ro  single
initrd		/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		99550239-9eb2-425f-915c-91aaebcc129b
kernel		/vmlinuz-2.6.31-14-generic root=UUID=a724b9d5-40a3-4408-850d-5b99f4b09c7c ro quiet splash 
initrd		/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		99550239-9eb2-425f-915c-91aaebcc129b
kernel		/vmlinuz-2.6.31-14-generic root=UUID=a724b9d5-40a3-4408-850d-5b99f4b09c7c ro  single
initrd		/initrd.img-2.6.31-14-generic

title		Chainload into GRUB 2
root		99550239-9eb2-425f-915c-91aaebcc129b
kernel		/boot/grub/core.img

title		Ubuntu 9.10, memtest86+
uuid		99550239-9eb2-425f-915c-91aaebcc129b
kernel		/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

#Window 7
title WinDOHws 7 Ultimate 
rootnoverify (hd0,3) # This is the location of the windows partition
makeactive
chainloader +1

```

---

### Post by hwttdz on 2009-11-20
You're probably using grub2, check out this howto [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

To check if you're using grub2 run "grub-install --version" if it's GNU GRUB 1.97 that's grub2.

---

### Post by Gorf on 2009-11-20
It appears to be 0.97:

gorf@gorf-laptop:~$ grub-install --version
grub-install (GNU GRUB 0.97)

I will check out that link.

---

### Post by hwttdz on 2009-11-20
The link is primarily a grub2 how to.  So it won't address your grub 1 problem.

---

### Post by Gorf on 2009-11-20
Well wait a minute... if I read that link correctly then the Grub that is installed as the boot manager is Grub 2.  Section 2: First Look Differences describes the behaviour of my Grub install perfectly.  But the tools that are installed in the OS clearly show I am on 0.97.  I'm going to try the "shift" key trick and see if I can get into the menu.  Maybe I have the install all f'ed up when I tried to reinstall Grub.

---

### Post by Gorf on 2009-11-20
Ok for reference I see what the problem is.  For starters when I installed grub I did "apt-get install grub" when I should have used the packaged grub2.  Consequently when I did "update-grub" it wrote a new menu.lst file which doesn't work with grub2.  Now that I have installed grub2, everything is honky-dory when I run update-grub.

---

