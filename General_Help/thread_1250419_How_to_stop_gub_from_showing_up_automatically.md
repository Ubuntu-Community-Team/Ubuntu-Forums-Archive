---
title: "How to stop gub from showing up automatically"
date: 2009-08-26
forum: General Help
---

### Post by tkblackbelt on 2009-08-26
Does anyone know how to make the grub menu only show up when you press esc on boot

---

### Post by coldReactive on 2009-08-26
Show us your **/boot/grub/menu.lst**

---

### Post by ajgreeny on 2009-08-26
Edit the /boot/grub/menu.lst ```
gksudo gedit /boot/grub/menu.lst
```to remove the # (ie uncomment) from the line #hiddenmenu line 24 in mine.  I think the line was a bit different in previous versions of ubuntu, but it was still self-explanatory.

---

### Post by tkblackbelt on 2009-08-26
Heres my menu.lst

-------------------------------------------
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
# kopt=root=UUID=9f860c0b-5b7b-41b5-949f-b1188155b397 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9f860c0b-5b7b-41b5-949f-b1188155b397

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
uuid        9f860c0b-5b7b-41b5-949f-b1188155b397
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=9f860c0b-5b7b-41b5-949f-b1188155b397 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        9f860c0b-5b7b-41b5-949f-b1188155b397
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=9f860c0b-5b7b-41b5-949f-b1188155b397 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, memtest86+
uuid        9f860c0b-5b7b-41b5-949f-b1188155b397
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by DeMus on 2009-08-26
> **chuckbenger said:**
> Does anyone know how to make the grub menu only show up when you press esc on boot

In /boot/grub/menu.lst you find this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Erase the # in front of the last line.


This is the way to do it:

Open a terminal: Applications > Accessories > Terminal
Type
gksudo gedit /boot/grub/menu.lst

Type your password.

Then edit the file and save it.
When finished you can try a reboot.

---

### Post by tkblackbelt on 2009-08-26
> **DeMus said:**
> In /boot/grub/menu.lst you find this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```Erase the # in front of the last line.


This is the way to do it:

Open a terminal: Applications > Accessories > Terminal
Type
gksudo gedit /boot/grub/menu.lst

Type your password.

Then edit the file and save it.
When finished you can try a reboot.


Thank you very much that worked:)

---

### Post by downart on 2010-12-08
i cant find that file. when i open it with the terminal it gives me a blank document and when i search for it manually it isnt there.

thanks

---

### Post by drs305 on 2010-12-08
> **downart said:**
> i cant find that file. when i open it with the terminal it gives me a blank document and when i search for it manually it isnt there.

thanks

downart,

Welcome to the Ubuntu forums.

You are most likely using Grub 2. It's a major change from the way Grub legacy worked and it's files are different.

The menu file is now /boot/grub/grub.cfg, but you edit the /etc/default/grub file to change the settings.

```
gksu gedit /etc/default/grub
```

Normally you would just need to set GRUB_TIMEOUT= to 0 in that file. I would recommend you leave it for a second or two so you can interrupt it if necessary.

To learn more about Grub2, click on the G2-Basics link in my signature line.

For a GUI way to set the timeout and default OS, you can install and use *startupmanager*. After installation, it's under System, Administration, Startup Manager. There is a link for SUM in my signature line as well.

---

### Post by downart on 2010-12-08
it seems to be set to 0 already.

---

### Post by drs305 on 2010-12-08
> **downart said:**
> it seems to be set to 0 already.


If your /etc/default/grub setting is " GRUB_TIMEOUT=0 " and you didn't have to change it, the next time you boot check to see if you see any counter timing down the seconds. Chances are you won't. If you changed the value from 10 to 0, did you run "sudo update-grub" after making the change?

If the screen just appears with no countdown, it is likely your Grub2 is triggering a 'recordfail' event. It does this when G2 detects some problem with your system and stops at the menu to allow you to select an entry.

Let's try to reset the recordfail, if it exists, and then temporarily change /boot/grub/grub.cfg to remove the recordfail check. (Normally we don't edit this file). The first command will reset any existing recordfail, the second will open grub.cfg for editing.

```
sudo grub-editenv create
gksu gedit /boot/grub/grub.cfg
```

Then find this section around line 56:
> 
if [ "${recordfail}" = 1 ]; then
  set timeout=**[COLOR="Red"]-1[/COLOR]**
else
  set timeout=0
fi

and change it to:
> 
if [ "${recordfail}" = 1 ]; then
  set timeout=**[COLOR="Red"]0[/COLOR]**
else
  set timeout=0
fi

Save the file and reboot. Do NOT run the update-grub command, as it would overwrite the change you just made.

If it was a recordfail problem, your system should boot without you seeing the menu. Let us know the result.

If it still doesn't boot without displaying the menu, post the contents of RESULTS.txt after running *meierfra's* boot info script, found here:
[_[U]http://bootinfoscript.sourceforge.net_[/U]]("http://bootinfoscript.sourceforge.net")

---

### Post by sammiev on 2010-12-08
This was my default

if [ "${recordfail}" = 1 ]; then
set timeout=-1
else
set timeout=10
fi 


After changes which only shows the screen for 1 second

if [ "${recordfail}" = 1 ]; then
set timeout=-1
else
set timeout=1
fi 

Good Luck :)

---

### Post by drs305 on 2010-12-08
> **sammiev said:**
> This was my default

Good Luck :)

sammiev,

Just so there is no confusion, you would not normally edit grub.cfg. The change you made in the 'recordfail' section would usually be made to the GRUB_TIMEOUT entry in /etc/default/grub.

We were just changing the recordfail value from -1 to 0. The -1 value will stop the menu from continuing until a selection is made; so we are bypassing that check and telling it to boot without delay even if a recordfail event is found. And we are only doing this as a test.

---

### Post by sammiev on 2010-12-08
> **drs305 said:**
> sammiev,

Just so there is no confusion, you would not normally edit grub.cfg. The change you made in the 'recordfail' section would usually be made to the GRUB_TIMEOUT entry in /etc/default/grub.

We were just changing the recordfail value from -1 to 0. The -1 value will stop the menu from continuing until a selection is made; so we are bypassing that check and telling it to boot without delay even if a recordfail event is found. And we are only doing this as a test.

Thank you are the update sir! :)

---

