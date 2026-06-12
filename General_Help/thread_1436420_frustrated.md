---
title: "frustrated"
date: 2010-03-22
forum: General Help
---

### Post by frustrated43 on 2010-03-22
i had ubuntu jaunty jackalope and windows xp on my dell ispiron. a friend split my hard drive beacuse i wasn't sure about ubuntu. he installed using a cd. a few weeks ago i updated to karmic koala. not thinking ..i did it from the site, which took my whole hard drive. question..is it a difficult process to get back the jaunty jackalope and windows xp or is it gone forever? also music situation is completely frustrating, otherwise i might keep ubuntu. i was told that using banshee or rhythm box was simple to use ipod with...it has not proven anything but to be a frustration.  please help :(

---

### Post by oldos2er on 2010-03-22
If you want Jaunty, you'll need to reinstall it. Do you still have a WinXP partition? Please post the output of ```
sudo fdisk -l
``` run in a terminal.

---

### Post by frustrated43 on 2010-03-22
i'm sorry i have no clue what "output" of code means. my friend had split the hard drive so that i could have jaunty jackalope and windows xp. he installed the ubuntu jj fron a disk. a few weeks ago i updated to karmic koala from the site thinking it would just update and keep the split. now my windows xp is gone. i only have karmic koala.

---

### Post by frustrated43 on 2010-03-22
> **oldos2er said:**
> If you want Jaunty, you'll need to reinstall it. Do you still have a WinXP partition? Please post the output of ```
sudo fdisk -l
``` run in a terminal.
sry you meant this?Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9f9aa9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1918       19866   144171888    7  HPFS/NTFS
/dev/sda4           19867       30401    84622387+   5  Extended
/dev/sda5           19867       30237    83304994+  83  Linux
/dev/sda6           30238       30401     1317298+  82  Linux swap / Solaris

---

### Post by oldos2er on 2010-03-22
So your XP partitions are still there. Do you know which version of grub you're using? I'm guessing it would be legacy grub...? I'm wondering if Windows is refusing to boot since apparently its boot partition is no longer the first primary partition, according to the fdisk info.

---

### Post by frustrated43 on 2010-03-22
> **oldos2er said:**
> So your XP partitions are still there. Do you know which version of grub you're using? I'm guessing it would be legacy grub...? I'm wondering if Windows is refusing to boot since apparently its boot partition is no longer the first primary partition, according to the fdisk info.
i'm looking but nothing with that name comes up. how would i find out..about grub that is? so i still have my windows xp?? i thought i lost all my music and picturrres lol

---

### Post by frustrated43 on 2010-03-22
i went to gparted and there are 2 partions. clicked on smaller partion and hit boot. nothing seemed to change. anytime i search word "grub" i only get it under "install software"

---

### Post by Mark Phelps on 2010-03-22
Relax ... know it's frustrating ... but first off, your XP is not "gone" and second, your files are still there.  So, you haven't really lost anything.

Most probably what happened is that your menu.lst file (the file that provides you the selection menu when you boot) got overwritten by a new version during the recent upgrade.  And new default versions don't include other OSs.

All you will have to do is edit your menu.lst file to add a "stanza" (fancy word for bunch of text lines) to describe your XP location, and when you save that and reboot, you'll have access to XP and Ubuntu back.

Sorry, I have to go right now.  I'm sure Oldos2er will get back to you with the details.  I'll check back tomorrow.

---

### Post by frustrated43 on 2010-03-22
hey mark..thanks. i want to learn ubuntu. so time consuming. really appreciate all the help. i'm searching to figure out how to do what you said. :)

---

### Post by DeMus on 2010-03-23
You know now how to open a terminal, do it again.
Type
```
more /boot/grub/menu.lst
```

Copy the whole text, select it with your cursor, and then type Shift-Ctrl-C (press and hold shift and ctrl, then press c)
paste it in your answer.

---

### Post by frustrated43 on 2010-03-23
Hi DeMus. want to make sure i understand you. is it the info that comes up after entering the code that you want me to paste and copy to send to you?

---

### Post by Chronon on 2010-03-23
Yes.  Enter that command in the terminal, then copy and paste (as instructed in DeMus's post) the output into your answer here.

---

### Post by audiomick on 2010-03-23
When you paste that output here, use the # button at the top of the posting window to put code tags around it. Click on the button, and paste the text in between the "code" and "/code" in square brackets that appear.

---

### Post by egalvan on 2010-03-23
> **frustrated43 said:**
> 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               [COLOR="Red"]1           5[/COLOR]       40131   de  Dell Utility
/dev/sda2              [COLOR="Red"] 6        1918 [/COLOR]   15360000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        [COLOR="Red"]1918       19866[/COLOR]   144171888    7  HPFS/NTFS

/dev/sda4           [COLOR="Red"]19867       30401[/COLOR]    84622387+   5  Extended
/dev/sda5           [COLOR="Red"]19867[/COLOR]       30237    83304994+  83  Linux
/dev/sda6           30238       [COLOR="Red"]30401[/COLOR]     1317298+  82  Linux swap / Solaris

The progression of start/end blocks shows

sda1 -> a Dell partition, probably vfat (probably a 'utilities' partition, given the small size)

sda2 -> a Windows NTFS partition, of medium size

sda3 -> a Windows NTFS partition, of much larger size

sda4 -> an extended partition, which holds
sda5 -> a Linux partition
sda6 -> a Linux swap partition


So it looks like your Windows stuff is still there.
olddos2er, demus, phelps, et.all. will get you back in good shape presto.

---

### Post by frustrated43 on 2010-03-23
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

---

### Post by DeMus on 2010-03-23
> **frustrated43 said:**
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

If this the whole of your menu.lst file then something is definitely wrong.
Please try again with the same command and now copy the whole of the file, scroll the screen if you have to cause what you posted out here is only a part of the file. The best part is missing.

---

### Post by oldos2er on 2010-03-23
Try **cat /boot/grub/menu.lst**

You'll probably need to scroll up in the terminal to grab all the output.

---

### Post by Serpher on 2010-03-23
Either that or you can use replace 'more' with 'gedit'

```
gedit /boot/grub/menu.lst
```


Much easier to use.


Also try going to Places and look for something like "80G Media". It might be your Window's partition where all your files are.

---

### Post by frustrated43 on 2010-03-23
ok every one. this is the whole thing

norine@norine-laptop:~$ more /boot/grub/menu.lst
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
--More--(15%)

---

### Post by frustrated43 on 2010-03-23
this is what i got replacing with "getit"

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
# kopt=root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff66e164-162b-473d-86ae-58377fa9d40c

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by frustrated43 on 2010-03-23
someone also had suggested using easybcd. i've no clue lol

---

### Post by oldos2er on 2010-03-23
You'll need to edit your menu.lst ```
gksu gedit /boot/grub/menu.lst
``` and create an entry for Windows; something like what appears under "examples"

title Windows 95/98/NT/2000
root (hd0,3)
makeactive
chainloader +1

Add that to the end of the file, save, exit, and reboot. Let us know if it works or not.

---

### Post by frustrated43 on 2010-03-24
i'm going to do what you suggest right now. but need to know when you say "and create an entry for Windows; something like what appears under "examples"..do you mean for me to type that in exactly what is there - title Windows 95/98/NT/2000
root (hd0,3)
makeactive
chainloader +1



but enter my version of windows?  sorry i am totally new here and don't have a clue lol

---

### Post by oldos2er on 2010-03-24
Copy and paste it. You can change the title to whatever you like.

---

### Post by frustrated43 on 2010-03-24
i changed title to windows xp that did not work

---

### Post by Colo2 on 2010-03-24
Open the file, Make sure its there. 

If it's not, do as oldos2er said:

title Windows 95/98/NT/2000
root (hd0,3)
makeactive
chainloader +1

Changing the title won't make it not work

---

### Post by frustrated43 on 2010-03-24
coped and pasted then changed title to windows xp did not work. also just clicked on a file on my ubuntu desktop titled OS. it is all of windows ..why would that be there? and how did it get there LOL

---

### Post by frustrated43 on 2010-03-24
um open what file?

---

### Post by Colo2 on 2010-03-24
> **frustrated43 said:**
> coped and pasted then changed title to windows xp did not work. also just clicked on a file on my ubuntu desktop titled OS. it is all of windows ..why would that be there? and how did it get there LOL

did you save the file before closing it? and also is there a windows disk in your CD Drive?

---

### Post by frustrated43 on 2010-03-24
yep i saved it.  :) and no i do not have a windows cd in my drive. i do not even have a windows cd

---

### Post by oldos2er on 2010-03-24
> **frustrated43 said:**
> coped and pasted then changed title to windows xp did not work. 

Can you give more info? You reboot, select WinXP from the grub menu, and what exactly happens?

---

### Post by frustrated43 on 2010-03-24
i coped and pasted again. this time typing in title WinXp. yes i saved it. i restart computer move arrows to WinXp and hit enter. tells me invalid request

---

### Post by oldos2er on 2010-03-24
You can try Super grub disk to restore Windows' MBR, which should allow you to get back to Windows. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Sorry I wasn't able to help you out more.

---

### Post by Serpher on 2010-03-24
I'm using the GRUB for Ubuntu 9.10, which is a little different but the important parts are all the same.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set cb99ca47-a858-4639-a5a7-aa0778bbd123
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cb99ca47-a858-4639-a5a7-aa0778bbd123
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=cb99ca47-a858-4639-a5a7-aa0778bbd123 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cb99ca47-a858-4639-a5a7-aa0778bbd123
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=cb99ca47-a858-4639-a5a7-aa0778bbd123 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1cc8a3adc8a3841c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

It'll be at the very bottom. First I would just make sure you have those brackets '}' correct by looking at mine before copy pasting because again, it might be a little different. Also before modifying it could you post grub.cfg again so we can see if it was put in correctly and all the brackets are in the right place.

---

### Post by frustrated43 on 2010-03-25
here it is serpher. this is the entire section. i have 2 apptmnts today so i won't be back until about 3 my time (calif) although i'm wanting to just get this alll over with already lol any help given is much MUCH appreciated. oh and i am using ubuntu 9.10. i updated from jaunty jackalope. which is when this problem started.


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
# kopt=root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff66e164-162b-473d-86ae-58377fa9d40c

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by oldos2er on 2010-03-25
There's no Windows stanza there? Thought you said you edited it to add one.

---

### Post by frustrated43 on 2010-03-25
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
# kopt=root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff66e164-162b-473d-86ae-58377fa9d40c

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title WinXp
root (hd0,3)
makeactive
chainloader +1

---

### Post by frustrated43 on 2010-03-25
i just moved copied/pasted part above  the ### END DEBIAN AUTOMAGIC KERNELS LIST . saved then restarted. that didn't change anything either. still says invaled request


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
# kopt=root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff66e164-162b-473d-86ae-58377fa9d40c

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/memtest86+.bin
quiet

title WinXp
root (hd0,3)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by frustrated43 on 2010-03-25
this is my third try today.

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
# kopt=root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff66e164-162b-473d-86ae-58377fa9d40c

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/memtest86+.bin
quiet

#title WinXp
#root (hd0,3)
#makeactive
#chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by frustrated43 on 2010-03-25
4th try  today

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
# kopt=root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff66e164-162b-473d-86ae-58377fa9d40c

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/memtest86+.bin
quiet

#title           WinXp
#root            (hd0,3)
#makeactive
#chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by frustrated43 on 2010-03-25
this is my 4th try today. first one (for the 4th try) didn't copy the way it looks. anyway..this is the 4th try

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
# kopt=root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ff66e164-162b-473d-86ae-58377fa9d40c

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ff66e164-162b-473d-86ae-58377fa9d40c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ff66e164-162b-473d-86ae-58377fa9d40c
kernel        /boot/memtest86+.bin
quiet

#title           WinXp
#root            (hd0,3)
#makeactive
#chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by frustrated43 on 2010-03-25
it isn't showing up for some reason but with the 4th try i spaced between #title             WinXp    etc

---

### Post by oldos2er on 2010-03-26
It isn't showing up because you need to remove the # comment marks from the front of each line. Sorry I didn't notice that sooner.

---

### Post by matchett808 on 2010-03-27
if it doesn't work with "root            (hd0,3)" then try "root            (hd0,2)"

---

### Post by frustrated43 on 2010-03-28
ok so i removed the # comment mark and then changed hd0,3 to hd0,2     voila..windows back..that's nuts. so simple. why si many headaches in the process? lol so i thinking of taking the class that is offered here at ubuntu...so maybe i can know what the heck i am doing lol

---

### Post by frustrated43 on 2010-03-30
wanted to come back and thank all who helped me..thank you :)

---

