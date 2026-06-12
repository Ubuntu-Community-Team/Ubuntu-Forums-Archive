---
title: "Changing GRUB priority"
date: 2006-02-19
forum: General Help
---

### Post by ro88o on 2006-02-19
I've installed Ubuntu and when GRUB comes up it is the highlighted option but I want to change this so I can switch my computer on and it will automatically load Windows XP by default. What do I have to do to change this ?

TIA, Tom

---

### Post by knalle on 2006-02-19
emacs /boot/grub/menu.lst

grub-install /dev/disk

---

### Post by kaamos on 2006-02-19
```
sudo gedit /boot/grub/menu.lst
```
Find a section that looks like this
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

and change it to this
> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		saved

Now grub will boot the last selected os by default. You can also use the number (count the os's starting from the top. The first one is 0)

---

### Post by malic on 2006-02-19
[QUOTE=kaamos]```
sudo gedit /usr/boot/grub/menu.lst
```
Find a section that looks like this

and change it to this

Now grub will boot the last selected os by default. You can also use the number (count the os's starting from the top. The first one is 0)[/QUOTE]

I typed `sudo gedit /usr/boot/grub/menu.lst` command into terminal but an empty notepadlike window opened/ i could not find related info typings to change/:D ;)

---

### Post by kaamos on 2006-02-19
Whoops!! My bad, typoed. The path should be /boot/grub/menu.lst

---

### Post by malic on 2006-02-19
Now it says that access was denied

---

### Post by kaamos on 2006-02-19
Thats strange.. Are you shure you had sudo in front of the command? If so, try "sudo nautilus" and navigate to the folder (/boot/grub) and look for the file (menu.lst).

---

### Post by malic on 2006-02-19
Dear Kaamos i am new to linux/ Now i will explain what i did/

I logged on ubuntu as user then opened terminal and typed **sudo gedit /boot/grub/menu.lst ** into terminal and pressed enter. My password was asked then entering correctly i reached an empty menu.lst notepadlike document

---

### Post by malic on 2006-02-19
\\:D/  oooo... Now i a full document displayed like below

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by steve.horsley on 2006-02-19
The easiest thing to do is to move the last 7 lines: > # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1 ans put them between these two lines instead:
> # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LISTThis will put windows at the top of the list of choices when you boot.

---

### Post by malic on 2006-02-19
Thanks Steve, i operated process like your explaination. And also thank you Kaamos:D

---

### Post by Varko on 2007-12-22
Cutting and pasting the Windows entry before the Ubuntu entry is a little risky.  In today's update of the kernel the update process rebuilt /boot/grub/menu.lst and deleted the Windows XP entry that I had moved to the first spot.  I had to redo that entry to boot Windows.  Instead of moving the Windows entry, I recommend changing the line that reads 
default 0
to default 4
assuming that the Windows XP line is the 5th line in the grub menu as in the example above.  The first line is 0, and you count the line that says "Other operating systems".

---

### Post by meierfra on 2007-12-22
> Cutting and pasting the Windows entry before the Ubuntu entry is a little risky.

Varko, you must have put the Windows entry after the line

### BEGIN AUTOMAGIC KERNELS LIST

If it is before that line, there will be   problems with  kernel updates.

---

