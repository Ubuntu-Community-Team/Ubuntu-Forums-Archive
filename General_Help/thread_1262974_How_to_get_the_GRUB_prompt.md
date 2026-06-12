---
title: "How to get the GRUB prompt"
date: 2009-09-10
forum: General Help
---

### Post by smallbear on 2009-09-10
I keep reading information suggesting that there is a recovery mode available from the GRUB prompt, which I assume is a prompt at boot-up.  How do I get my machine *(9.04 Desktop - No Windows install, just Ubunto)* to show this prompt?  Mine boots directly to the Ubuntu login and doesn't seem to show me anything more.  Many thanks.

---

### Post by plucky on 2009-09-10
> **smallbear said:**
> I keep reading information suggesting that there is a recovery mode available from the GRUB prompt, which I assume is a prompt at boot-up.  How do I get my machine *(9.04 Desktop - No Windows install, just Ubunto)* to show this prompt?  Mine boots directly to the Ubuntu login and doesn't seem to show me anything more.  Many thanks.

It should show you the GRUB menu unless you have it hidden.

Recovery mode should be the second item in the menu list and boots into a menu to fix problems.It is selected using the arrow keys when the menu appears.

Open a terminal and post output of ```
cat /boot/grub/menu.lst
```so we can see how your grub is setup.

---

### Post by mcduck on 2009-09-10
> **smallbear said:**
> I keep reading information suggesting that there is a recovery mode available from the GRUB prompt, which I assume is a prompt at boot-up.  How do I get my machine *(9.04 Desktop - No Windows install, just Ubunto)* to show this prompt?  Mine boots directly to the Ubuntu login and doesn't seem to show me anything more.  Many thanks.

It should show a message that tells you to press Esc key to show the Grub menu. This message will appear as white text on black screen and lasts 3 seconds.

Unless you have some problem with graphics that would prevent it from being visible it's definitely there, you'll just have to pay attention during the bootup. (it's not possible to completely remove the Grub menu, you'll always get either the menu or this message for showing the menu).

---

### Post by Screwdriver0815 on 2009-09-10
you have to hit "esc" when the dialog "press ESC to enter the menu" comes up. This dialog is connected with a countdown and when you do not hit the esc key it continues booting.

When you hit the esc-key, the booting stops and you can choose in the grub menu what you want to run

---

### Post by smallbear on 2009-09-11
> **plucky said:**
> Open a terminal and post output of ```
cat /boot/grub/menu.lst
```so we can see how your grub is setup.

Hi, many thanks.  The menu.lst file is below.

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=020e87dc-8308-40d1-8b8c-d64bb821f962 ro rootdelay=10

## default grub root device
## e.g. groot=(hd0,0)
# groot=020e87dc-8308-40d1-8b8c-d64bb821f962

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
uuid        020e87dc-8308-40d1-8b8c-d64bb821f962
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=020e87dc-8308-40d1-8b8c-d64bb821f962 ro rootdelay=10 quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        020e87dc-8308-40d1-8b8c-d64bb821f962
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=020e87dc-8308-40d1-8b8c-d64bb821f962 ro rootdelay=10  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        020e87dc-8308-40d1-8b8c-d64bb821f962
kernel        /boot/memtest86+.bin
quiet

---

### Post by plucky on 2009-09-11
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu



That is why you are not seeing the grub menu.

Edit the file and put a # in front of "hiddenmenu" and you should then see the grub menu or press <ESC> key when booting.

The recovery mode is the second item on the list.

> title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)

Also your timeout value is quite low > timeout 3 so you will have only 3 seconds to select the recovery mode.

Good Luck

> kernel 2.6.28-11-generic  Your kernel version  seems to be quite old,have you updated lately.

---

### Post by mcduck on 2009-09-11
> **plucky said:**
> That is why you are not seeing the grub menu.

Edit the file and put a # in front of "hiddenmenu" and you should then see the grub menu or press <ESC> key when booting.

The recovery mode is the second item on the list.



Also your timeout value is quite low  so you will have only 3 seconds to select the recovery mode.

Good Luck

  Your kernel version  seems to be quite old,have you updated lately.

Actually the hiddenmenu option is hwat changes Grub from automatically showing the menu into showing the message about pressing Esc instead. So no, there's no need to remove the hiddenmenu option unsess you want to show the menu by default.

Like I said, it's not possible to completely hide Grub. you either get the menu, or you get the message that tells you to press Esc to show the menu.

Even using zero timeout won't do that, since any value lower than 3 seconds will simply result in the 3 seconds timeout.

---

### Post by smallbear on 2009-09-11
> **plucky said:**
> Your kernel version  seems to be quite old,have you updated lately.

Many thanks to all for the help.  I have now set the menu option - it used to show this as standard on a previous version of Ubuntu.  This one is 9.04 and only downloaded about a week ago and appears to have been changed in that respect.

This leads me to my next question.  You mention the kernel being old.  Why is this, because it's a new download of Ubuntu Desktop, from the official site?  I puzzled here.

---

### Post by plucky on 2009-09-11
> This leads me to my next question. You mention the kernel being old. Why is this, because it's a new download of Ubuntu Desktop, from the official site? I puzzled here.

The Ubuntu download CD came out in April and that doesn't get upgraded until the next release (Karmic).Any kernel and software upgrades are loaded into the repositories and upgrades are done online.

Your kernel is at 2.6.28-11 whereas my kernel for Jaunty is at 2.6.28-15,which is why I said your kernel is out of date. If you have a fast broadband connection,open a terminal and ```
sudo apt-get update
``` will show you how many updates are available.```
sudo apt-get upgrade
``` will download and upgrade your system.


Good Luck

---

### Post by smallbear on 2009-09-12
> **plucky said:**
> The Ubuntu download CD came out in April and that doesn't get upgraded until the next release (Karmic).

Many thanks Plucky, it didn't occur to me that the download was set to April's release.  You've enlightened me there.

---

### Post by smallbear on 2009-09-14
> **plucky said:**
> Your kernel is at 2.6.28-11 whereas my kernel for Jaunty is at 2.6.28-15

I have updated my kernel with sudo apt-get update, followed by sudo apt-get upgrade and all appears to be well.

However, the /boot/grub/menu.lst file has not changed, which was the file from which we realised my kernel was out of date, last week.

Should this file change?

How can I check to see my Kernel version another way?  Many thanks.

---

### Post by plucky on 2009-09-14
> Should this file change?


Yes, What does terminal command ```
cat /boot/grub/menu.lst
uname -a
``` show?

Good Luck

---

### Post by stephen.robin on 2009-09-14
Hi

GRUB stands for GRand Unified Bootloader. It's meant as a alternative to the widely-used LILO (LInux LOader). In many ways, it is superior to LILO. One such advantage of GRUB is that if the configuration file is incorrect or corrupted, you may still be able to boot your system. It does require a basic familiarity with using GRUB in Interactive mode. This tip is meant to help you do that.
:lolflag::KS

---

