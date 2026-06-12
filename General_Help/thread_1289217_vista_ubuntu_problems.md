---
title: "vista ubuntu problems"
date: 2009-10-12
forum: General Help
---

### Post by VuduMunky on 2009-10-12
i updated ubuntu from 9.04 to 9.10 using update manager, and after a reboot i got the grub error 22, i googled and found a few things that might help me but none did.
after messing for a few hours i decided to download the 9.10 live cd and booted it up and tried 2 access my vista partition but it popped up a msg box asking for a password but i was using the live cd so i had no password to enter, next i opened gparted and was told from there that i couldn't access the vista partition because it had 3 errors on it, it said i had to run checkdisk from windows so i booted up my recovery disk that came with the laptop and did what was requested and booted up the live cd again problem solved i could now see the vista partition from ubuntu and access files on it, so i proceeded to install 9.10 all went well until reboot. i got the option to choose vista(loader) but nothing would happen when selected i am no expert but was convinced it was a grub2 problem so i removed grub2 and replaced it with grub so i could edit the menu.1st which is gone from grub2 again everything seemed to go well after i added the entry to menu.1st so i rebooted hit vista and it just says starting but never gets past that, after this i got myself a copy of supergrub boot cd and tied everything possible but still no joy please can somebody point me in the right direction, i cant do a clean install of vista as i have 125gb of stuff that is not backed up. sorry for the long winded explanation.

---

### Post by Ekeluo on 2009-10-12
Are you still on grub (1)? If so, post your menu.lst. Also, after running your recovery cd, could/did you boot into Vista successfully? We need to know if the problem lies with Grub or Vista boot-up.

---

### Post by VuduMunky on 2009-10-12
thanks 4 the quick reply, yes i am still using grub1 and here is the contents of menu.1st and i have not been able to boot into vista since running the upgrade from update manager.

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
# kopt=root=UUID=dccf55f7-f6fc-47ac-a67b-a8d5dbc7ad0a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dccf55f7-f6fc-47ac-a67b-a8d5dbc7ad0a

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

title        Ubuntu karmic (development branch), kernel 2.6.31-11-generic
uuid        dccf55f7-f6fc-47ac-a67b-a8d5dbc7ad0a
kernel        /boot/vmlinuz-2.6.31-11-generic root=UUID=dccf55f7-f6fc-47ac-a67b-a8d5dbc7ad0a ro quiet splash 
initrd        /boot/initrd.img-2.6.31-11-generic
quiet

title        Ubuntu karmic (development branch), kernel 2.6.31-11-generic (recovery mode)
uuid        dccf55f7-f6fc-47ac-a67b-a8d5dbc7ad0a
kernel        /boot/vmlinuz-2.6.31-11-generic root=UUID=dccf55f7-f6fc-47ac-a67b-a8d5dbc7ad0a ro  single
initrd        /boot/initrd.img-2.6.31-11-generic

title        Ubuntu karmic (development branch), memtest86+
uuid        dccf55f7-f6fc-47ac-a67b-a8d5dbc7ad0a
kernel        /boot/memtest86+.bin
quiet

title        Vista
root        (hd0,2)
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Ekeluo on 2009-10-12
Your Vista entry should be outside the linux kernels list zone, i.e., below the '### END DEBIAN AUTOMAGIC KERNELS LIST' line. Change and try again.

---

### Post by VuduMunky on 2009-10-12
thankyou i will try that and report back

---

### Post by VuduMunky on 2009-10-12
i edited the menu.1st and moved the vista entry but i still get the same thing when i select vista it just says starting up but hangs.:confused:

---

### Post by Ekeluo on 2009-10-12
Did you 'sudo update-grub after changing it?

---

### Post by VuduMunky on 2009-10-12
yes i did and it said it found ubuntu and memtest but no mention of vista but the option to select vista is still there and still doesn't work.

---

### Post by Ekeluo on 2009-10-13
I think your vista install might be borked. Problem doesn't seem to be from ubuntu/grub. Can you afford to rewrite the boot record with the windows version? (Can't help you with this tho)

---

### Post by VuduMunky on 2009-10-13
Vista is gone(good riddance), deleted its partition, going to start again i originally wanted to dual boot with XP but this laptop is only 3 mths old and i cant find all the drivers i need for XP, i only use window$ for 1 thing and if ubuntu had an alternative to it i would rid myself of micro$oft for good, anyways thanks for your time Ekeluo appreciated.:P

---

