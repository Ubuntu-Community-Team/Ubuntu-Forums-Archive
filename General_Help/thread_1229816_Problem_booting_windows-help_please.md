---
title: "Problem booting windows-help please"
date: 2009-08-02
forum: General Help
---

### Post by shajip88 on 2009-08-02
hi i have installed windows and then installed ubuntu. Now i cannot boot windows. I have only one drive 160Gb.. I have read the previous threads with the same problem and tried the commands but it never worked. Are the commands depend upon the system config? please help me.

---

### Post by merlinus on 2009-08-02
Open a terminal and post results of these commands:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```You will find the terminal listed in Applications/Accessories.

l is a lowercase L

---

### Post by shajip88 on 2009-08-02
shaji@shaji:~$ sudo fdisk -l
[sudo] password for shaji: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc3cfc3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2423    19462716   83  Linux
/dev/sda3            2424       19456   136817572+   f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101       11474    51199123+   7  HPFS/NTFS
/dev/sda7           11475       19456    64115383+   7  HPFS/NTFS
/dev/sda8            2424        2550     1020064+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by shajip88 on 2009-08-02
shaji@shaji:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=09169e8f-234e-476d-9f69-8e670f4f564a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=09169e8f-234e-476d-9f69-8e670f4f564a ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=09169e8f-234e-476d-9f69-8e670f4f564a ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-08-02
You seem to have three ntfs partitions, sda5, sda6, and sda7.  Which one is windows?

Another problem is that all these are logical partitions, and windows wants to be on a primary.

But if you can tell us which of the three is windows, then an entry for menu.lst can be created that may allow you to access it.

---

### Post by shajip88 on 2009-08-02
sda5

---

### Post by merlinus on 2009-08-02
Add this to the end of menu.lst:

title Windows
rootnoverify (hd0,4)
makeactive
chainloader +1

Then change this:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]hiddenmenu[/COLOR]

to this:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]# hiddenmenu[/COLOR]

and restart.

Edit the file with this command:

```
gksudo gedit /boot/grub/menu.lst
```There should be a windows entry at the bottom of the grub menu.  Arrow down to it, press Enter, and report back as to what happens.

---

### Post by shajip88 on 2009-08-03
error 12 : invalid device requested

This is what i get after choosing windows and the part you asked me to change is same as the first one. c

---

### Post by nikhilk on 2009-08-03
> **shajip88 said:**
> error 12 : invalid device requested

This is what i get after choosing windows and the part you asked me to change is same as the first one. c

Are you absolutely sure that sda5 is your Windows boot partition? Can you mount it from Ubuntu and confirm (check for directories like WINDOWS, "Program Files", system32 etc)?

---

### Post by shajip88 on 2009-08-03
ya sure. I kept two 20Gb for windows and ubuntu. 19 Gb is for ubuntu and 20Gb for windows

---

### Post by merlinus on 2009-08-03
As I wrote earlier, windows will probably not run when it is on a logical partition, which is your situation.

---

### Post by shajip88 on 2009-08-03
so no other option than formatting and installing again?

---

### Post by merlinus on 2009-08-03
That is your easiest option, but this time be sure to install windows in the first primary partition.  And remember to back up important data first!

But for the heck of it, try this first, because your partitions are not in correct numerical order:

```
sudo fdisk /dev/sda
x
f
w
```

---

### Post by shajip88 on 2009-08-04
thank u

---

