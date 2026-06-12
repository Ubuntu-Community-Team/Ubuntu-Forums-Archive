---
title: "Automagic Kernel List Question"
date: 2009-07-21
forum: General Help
---

### Post by adempewolff on 2009-07-21
I edited my GRUB menu.lst a while ago to change the default choice, timeout length etc.  Since then whenever the update-manager downloaded a new kernel and it asked me if I wanted to replace my menu.lst (at the(ese) time(s) I wasn't paying attention and didn't notice it was downloading a new kernel or put two and two together why it was modifying my menu.lst) I said no because I didn't want to have to redo the my customizations.

The last time this happened right after I clicked the button I suddenly had the suspicion that I was actually preventing the automagic kernel list from updating and thus preventing myself from booting using the new kernels.  Comparing a "uname -a" with the contents of my /boot/ folder confirmed my fears.  (and made me feel like an idiot)

I'm fairly certain I can figure out how to add entries for the missing new kernels but I am curious about exactly how the automatic list works.  If I let it replace the old file would it disrupt my default choice and timeout length or would it keep those choices?

---

### Post by adempewolff on 2009-07-22
now I think I really might have broke something. sudo update-grub from the terminal find the two new kernels and says it updated grub

```
austin@austin-laptop:/boot/grub$ sudo cp menu.lst menu.lst.backup
austin@austin-laptop:/boot/grub$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

but does not actually add the two new Kernels...

I don't mind adding the new guys manually for now but am curious why the update-grub script isn't working.

heres my menu.lst for those interested:

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
default		1

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

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
# kopt=root=UUID=e3e5b648-18ea-41aa-a0ac-8571873e3f64 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e3e5b648-18ea-41aa-a0ac-8571873e3f64 xres=1280x800 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
savedefault

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e3e5b648-18ea-41aa-a0ac-8571873e3f64 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e3e5b648-18ea-41aa-a0ac-8571873e3f64 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e3e5b648-18ea-41aa-a0ac-8571873e3f64 ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e3e5b648-18ea-41aa-a0ac-8571873e3f64 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e3e5b648-18ea-41aa-a0ac-8571873e3f64 ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by jocko on 2009-07-22
Try this:

1. Rename your old menu.lst:```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
```(note that this temporarily leaves you without a menu.lst, so do not reboot at this stage).
2. Have update-grub make a new one:```
sudo update-grub
```(you will be told there is no menu.lst and asked if you want a new one to be generated, answer "y" for yes).
3. Change the behaviour of the boot menu to the way you want it:```
gksudo gedit /boot/grub/menu.lst.bak /boot/grub/menu.lst
```Change:```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR=Red]timeout        3[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]hiddenmenu[/COLOR]
```To:```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR=Red]timeout        10[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]#hiddenmenu[/COLOR]
```(and whatever else customizations you may want...)


4. Update-grub does not look for other operating systems, so if you still want to be able to boot your Dell utility partition you will need to copy everything after "### END DEBIAN AUTOMAGIC KERNELS LIST" from the old meny.lst to the new one.
Add this:```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```If this would not work out, just rename the backup to get the old menu back:```
sudo mv /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

---

