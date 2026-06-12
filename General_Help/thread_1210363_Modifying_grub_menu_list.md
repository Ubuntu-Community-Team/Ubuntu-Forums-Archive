---
title: "Modifying grub menu list"
date: 2009-07-11
forum: General Help
---

### Post by Nelbomber on 2009-07-11
Hey all, I am king newb to Ubuntu (v 9.04) and I am trying to change the boot order on my GRUB menu so it will auto boot into windows.  I found the menu.lst, but don't have permissions to save the file once I modify it.

I know the answer must be burried in here somewhere, but i havn't been able to find it yet.

I tried using the sudo command to open the file from terminal, but failed.  How to I log in as root and/or how do I use se this login to save my modified menu?

---

### Post by coffeecat on 2009-07-11
What you need is...

```
gksudo gedit /boot/grub/menu.lst
```

... from a terminal. That will give you the permissions you need to edit the file. Post back if you need help with what to edit in the file.

> **Nelbomber said:**
> How to I log in as root

Ouch! :evil:

Have a look at this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

:wink:

---

### Post by sisco311 on 2009-07-11
You can also install startupmanager, a grub and splash screen configuration tool.

---

### Post by Nelbomber on 2009-07-14
Thanks gents, I will try this out!

---

### Post by jskandhari on 2009-07-14
simple... just type
"sudo nautilus"
in the terminal/konsole
and guide your way to the file and open it edit it and save it....

Hope you get it done

---

### Post by jskandhari on 2009-07-14
simple... just type
"sudo nautilus"
in the terminal/konsole
and guide your way to the file and open it edit it and save it....

Hope you get it done

---

### Post by Nelbomber on 2009-09-30
Ok that worked wonderfully (Sorry for the late response i have been pretty busy lately).  I have removed all the extra versions of Ubuntu from there, but want to make sure I move whats left properly.  I am looking to have my Windows be the default boot option as I am still learning Linux and i keep accidentally booting into Linux.

This is what I currently have:

> title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
And I think this is what I want to do. Normally I would just try it, but I won't know how to fix it if I break it, its the 'quiet' commands that are making me question what I am to do.

> 
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Microsoft Windows XP Professional
#rootnoverify    (hd0,0)
#savedefault
#makeactive
#chainloader    +1


---

### Post by oboedad55 on 2009-09-30
> **Nelbomber said:**
> Ok that worked wonderfully (Sorry for the late response i have been pretty busy lately).  I have removed all the extra versions of Ubuntu from there, but want to make sure I move whats left properly.  I am looking to have my Windows be the default boot option as I am still learning Linux and i keep accidentally booting into Linux.

This is what I currently have:

And I think this is what I want to do. Normally I would just try it, but I won't know how to fix it if I break it, its the 'quiet' commands that are making me question what I am to do.

That should do the trick.

---

### Post by Nelbomber on 2009-09-30
Awesome thanks!

---

### Post by louieb on 2009-09-30
> **Nelbomber said:**
> 
This is what I currently have:...And I think this is what I want to do. 

I hope that not all of it. There is a reason for the lines above what you posted. They are used to build the new kernel entry when the kernel gets updated. 

As you have it now the upper windows entry will be erased come kernel update time. 
The proper place to copy your windows entry is between the lines. 

```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by Nelbomber on 2009-10-01
Hmmm thanks for catching that, but I don't completely follow where I should be putting the Windows boot.

Below are my entire GRUB file contents; if you could show me where to properly put the Windows boot I would be grateful.  I am assuming the '#' character is the comment out character, and if it is I think I have the windows boot in the right place.

Thanks All!

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#gksudo gedit /boot/grub/menu.lst
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
# kopt=root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8137ff81-5de8-4c5c-80be-6f81a4eeea13

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

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Microsoft Windows XP Professional
#rootnoverify    (hd0,0)
#savedefault
#makeactivegksudo gedit /boot/grub/menu.lst
#chainloader    +1


---

### Post by louieb on 2009-10-01
Took your menu.lst  moved the windows entry to where it needs to be to prevent it being deleted at kernel update time. 

BTW: the # does comment out a line. Except in the auto magic section it takes ## to comment the line.  (Don't know why - its a Debain update-grub thing) 

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#gksudo gedit /boot/grub/menu.lst
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
[COLOR=Red]title        Microsoft Windows XP Professional
 rootnoverify    (hd0,0)
 savedefault
 makeactive
 chainloader    +1[/COLOR]
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
# kopt=root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8137ff81-5de8-4c5c-80be-6f81a4eeea13

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
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=8137ff81-5de8-4c5c-80be-6f81a4eeea13 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        8137ff81-5de8-4c5c-80be-6f81a4eeea13
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title        Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
#title        Microsoft Windows XP Professional
#rootnoverify    (hd0,0)
#savedefault
#makeactivegksudo gedit /boot/grub/menu.lst
#chainloader    +1                      

```

---

