---
title: "Lost the MBR/hdd died"
date: 2009-07-26
forum: General Help
---

### Post by rodh on 2009-07-26
Help,  I can use SGD to get ubuntu running but it won't boot to an OS. I lost the C: drive (Windows) It was an Old 40 gig but it had my WinXP installed on it.  I am not to worried about the data or Windows lost as I am in getting ubuntu running again, ubuntu 9.04 is installed on a 250 Gig drive that I have made the first drive in BIOS setup but grub unable to find. And when I point it out the 9.04 searches and installs files needed to boot every time like part of it is missing.  I don't know how to fix it.

---

### Post by merlinus on 2009-07-26
It is possible to reinstall grub.  Post results of these whilst booted into ubuntu:
```

sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by rodh on 2009-07-26
bash: Sudo: command not found
rod@rod-desktop:~$

---

### Post by rodh on 2009-07-26
rod@rod-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue blink-white/blue

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
# kopt=root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash vga=794

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
# howmany=3

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 9.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

rod@rod-desktop:~$

---

### Post by merlinus on 2009-07-26
It looks like ubuntu used to be on your second hdd in the first partition.  That is now first hdd, first partition, so for starters change all the stanzas that look like this:

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

to

root (hd0,0)

and delete the windows ones at the end of the file.

Then change this line

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

to

# groot=(hd0,0)

BTW, sudo starts with a lowecase S, so that may be your problem.  

Then enter this in a terminal:

```
sudo grub
root (hd0,0)
setup (hd0)
quit

```remove the cd and restart.

---

### Post by rodh on 2009-07-26
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,0)

Error 22: No such partition

grub> setup (hd0)

Error 12: Invalid device requested

grub> root (hd0,0)

Error 22: No such partition

grub>

---

### Post by merlinus on 2009-07-26
Post results of

```
sudo fdisk -l
```

BTW, did you restart after editing menu.lst?

---

### Post by rodh on 2009-07-26
I can't remember how to edit grub

---

### Post by rodh on 2009-07-26
rod@rod-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x759deb84

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096b2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30150   242179843+  83  Linux
/dev/sdb2           30151       30515     2931862+   5  Extended
/dev/sdb5           30151       30515     2931831   82  Linux swap / Solaris
rod@rod-desktop:~$ 


**How do I edit those entries?**

---

### Post by merlinus on 2009-07-26
Don't, as it looks like ubuntu is indeed on (hd1,0).  Is that hdd now set to boot first in bios?

If so, let's try this for restoring grub:

```
sudo grub
root (hd1,0)
setup (hd1)
quit
```

and restart.

If we get grub working, then you can delete the windows entry.

---

### Post by rodh on 2009-07-26
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 


OK this did not fix grub, but I restarted and had to use SGD to restart and I was able to edit the (hd1,0) to (hd0,0).  Now I am going to try to reboot again without SGD.

---

### Post by merlinus on 2009-07-26
Is your ubuntu hdd set first in booting order in bios?

---

### Post by rodh on 2009-07-26
Yes,  Set that Last night thinking that Super Grub Disk would find and fix it in auto mode.

But, just in case I will reboot and check.

---

### Post by rodh on 2009-07-26
OK,  I checked and the boot sequence is DVD Rom, HDD 250 gig (for short)

---

### Post by rodh on 2009-07-26
Grub still giving me Error 22 Partition does not exist

      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,0)

Error 22: No such partition

grub>

---

### Post by merlinus on 2009-07-26
grub is now installed to the mbr of the linux hdd, which according to sudo fdisk -l is sdb.  So menu.lst should still be referring to it as root (hd1,0) in the linux stanzas.

You might try running the fdisk command once more to make sure.

---

### Post by rodh on 2009-07-26
rod@rod-desktop:~$ sudo fdisk -l
[sudo] password for rod: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096b2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30150   242179843+  83  Linux
/dev/sda2           30151       30515     2931862+   5  Extended
/dev/sda5           30151       30515     2931831   82  Linux swap / Solaris
rod@rod-desktop:~$

---

### Post by merlinus on 2009-07-26
Ok, now it is (hd0,0)

Try reinstalling grub once again:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

If this does not work, then the uuid for the linux partition has changed, and this will require further editing of menu.lst.

---

### Post by rodh on 2009-07-26
rod@rod-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue blink-white/blue

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
# kopt=root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash vga=794

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
# howmany=3

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-24-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 9.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[B]
 Merlinus,  I don't know how to edit menu.lst but I see alot of (hd1) stuff in there
[/B]

---

### Post by merlinus on 2009-07-26
```
gksudo gedit /boot/grub/menu.lst
```

Again, change all the linux roots to (hd0,0) and delete the windows lines at the end of the file, since you will no longer be running it.

---

### Post by rodh on 2009-07-26
examples
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

[B]
What about this line,  it is at the top[/B]

---

### Post by merlinus on 2009-07-26
No, they are there as examples.  You only want to delete the ones at the very end of menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by rodh on 2009-07-26
menu.lst - See: grub(8), info grub, update-grub(8)
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue blink-white/blue

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,0)
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
# kopt=root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash vga=794

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
# howmany=3

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-24-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro quiet splash vga=794 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a9e3fc0f-2b47-45e7-b26c-78236098cb54 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1


OK,  This is what it looks like now.  I am going to try to reboot

---

### Post by merlinus on 2009-07-26
Change this one too:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

the last line should be
# groot=(hd0,0)

If all this still does not work, then let's find the uuid for your linux partition and compare it with the menu.lst entries.

```
blkid
```

will show it.

---

### Post by rodh on 2009-07-26
OK, changed groot (hd0,0)

Now try to reboot.

---

### Post by rodh on 2009-07-26
Well that was fun,  Thanks for all the Help.  I rebooted just fine.

Although I do not know why Ubuntu is loading in a terminal enviroment?  I can watch what it is doing and it did not do that before this mess started. Really don't need to fix that I don't think. But is different than the splash screen with the progress bar.

OH, how do I mark this as Solved?

---

### Post by merlinus on 2009-07-26
Excellent!  And congrats for hanging in there through the process.

IIRC, go to your first post in this thread and add [SOLVED] to the beginning of the subject line.

---

### Post by rodh on 2009-07-26
Thanks Again!!!

---

