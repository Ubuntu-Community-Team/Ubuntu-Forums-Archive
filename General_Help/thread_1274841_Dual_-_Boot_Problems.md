---
title: "Dual - Boot Problems"
date: 2009-09-25
forum: General Help
---

### Post by Xycon on 2009-09-25
Hello, Newbie here...

I recently installed ubuntu after playing with it on live. I dual boot installed it, and it was working all fine and dandy, until I restarted my computer... At that point I noticed that there were duplicate dual boot options, and i figured that was kind of weird, that did not happen to the other computer I had Installed ubuntu on. So I shutdown, and tried running my windows vista (I know its vista, dont kill me please lol), well... it wasn't working really, it went through roughly 3 disk checks before I could actually boot it up.

So I guess my question is, should I uninstall Ubuntu all together and give up, uninstall Ubuntu, and try again, or try to debug my current situation?

Thanks for all help.

---

### Post by nikhilk on 2009-09-25
Lets see if we can get to the root of the problem.

Could you post the contents of your "/boot/grub/menu.lst" file and output of
```
sudo fdisk -l
```

---

### Post by Xycon on 2009-09-25
I'm sorry this is so big >.< i dont know what your looking for, again, i'm a newbie lol.


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
# kopt=root=UUID=1ff67a43-a098-4386-8705-8135420e36cd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1ff67a43-a098-4386-8705-8135420e36cd

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
uuid        1ff67a43-a098-4386-8705-8135420e36cd
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1ff67a43-a098-4386-8705-8135420e36cd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        1ff67a43-a098-4386-8705-8135420e36cd
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=1ff67a43-a098-4386-8705-8135420e36cd ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        1ff67a43-a098-4386-8705-8135420e36cd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1ff67a43-a098-4386-8705-8135420e36cd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        1ff67a43-a098-4386-8705-8135420e36cd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=1ff67a43-a098-4386-8705-8135420e36cd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        1ff67a43-a098-4386-8705-8135420e36cd
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by Xycon on 2009-09-25
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ee3248a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1448    11631028+   7  HPFS/NTFS
/dev/sda2            1449       37740   291515490    7  HPFS/NTFS
/dev/sda3           37741       38913     9422122+   5  Extended
/dev/sda5           37741       38857     8972271   83  Linux
/dev/sda6           38858       38913      449788+  82  Linux swap / Solaris

---

### Post by rreese6 on 2009-09-25
All of this looks ok.
Are you still having issues when you select Windows Vista?
the multiple Ubuntu Selections are normal. Each one does different things. when you upgrade your kernel it will add another set of two also.

---

### Post by nikhilk on 2009-09-25
As rreese6 said, the Ubuntu section looks OK. The multiple options are for multiple kernels installed and is perfectly normal.
One of the two Vista options might be wrong, I am guessing the bottom-most one. Uncomment all the lines (add a # in front on them) below these lines
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2

like this (the changes are in red)
```

[COLOR="Red"]#[/COLOR] title Windows Vista (loader)
[COLOR="Red"]#[/COLOR] rootnoverify (hd0,1)
[COLOR="Red"]#[/COLOR] savedefault
[COLOR="Red"]#[/COLOR] makeactive
[COLOR="Red"]#[/COLOR] chainloader +1

```
and try booting from the sole Windows entry and see how it goes.

---

### Post by Xycon on 2009-09-25
Oh jeez, I guess I was just being a noob then :\, so its normal to have two Windows load ups too? Yeah, Vista is working normally now, I guess it must have just been having a "vista" moment. 
Thank you for all your time and help!

Edit: Never mind on the two windows comment, solved above.

---

### Post by GnarlyGoat on 2009-09-25
I have a question along a similar topic. Whenever I boot up my PC, I get the option of choosing my vista partition and about 3 Ubuntu ones.  One of the posters above me mentioned that they were just different kernels of my Ubuntu install. I usually just pick the one that is at the top of the list and ignore the other 2. My question is this: is there a way to remove the other 2 kernels from the boot list?

The obvious thing to do would be to just comment out the unused kernels in the "Debian Automagic Kernels List" in the /boot/grub/menu.lst file. Is this what I'm supposed to do? Is there anything else that I should be aware of? Or is  my method a sure fire way of completly killing my boot-up process?

Any help on this would be appreciated.

---

### Post by awk on 2009-09-26
> The obvious thing to do would be to just comment out the unused kernels in the "Debian Automagic Kernels List" in the /boot/grub/menu.lst file. Is this what I'm supposed to do? Is there anything else that I should be aware of? Or is my method a sure fire way of completly killing my boot-up process?

You can indeed comment (#) the lines starting with "title", "uuid", "kernel" and "initrd" to (temporarily) remove a menu item. Feel free do so, it won't mess up anything.

However, it is good practice to make a backup of a configuration file before you change it. That way, if the change has unintended effects, you can revert the changes. (To do this you do of course need to be able to boot. If you mess up GRUB so bad that it won't boot, e.g. by commenting out *all* the menu entries, you can boot from a Live-CD and restore your original menu.lst from there.)

---

### Post by sale666 on 2009-09-26
@GnarlyGoat:

If you see multiple kernels and hate it (i do) you can remove them in synaptic!

Go in synaptic and write in linux-image xxxxxxx (i think its correct the x is the version)

And remove the ones you dont need! 
but DO NOT REMOVE THE ONE YOU ARE USING! 

Hope it helps! :guitar:

---

