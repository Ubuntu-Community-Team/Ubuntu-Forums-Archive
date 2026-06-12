---
title: "Grub loading... Error 17"
date: 2009-08-12
forum: General Help
---

### Post by esc0bar on 2009-08-12
Hey, I just got error 17 when starting up my computer.

I was running on:
Partition 1: Windows 7
Partition 2: Windows Vista
Partition 3: Ubuntu
Swap Partition

Everything was fine for a couple weeks. But, yesterday I decided to delete me Vista partition to have a FAt32 partition instead... so I could use files from this partition for both OS. Now, when I restart my computer, I get the error 17. Is there anything I can do to recuperate my seven and ubuntu partitions^

I<m currently booting from the Ubuntu CD.

Thank you.

Edit: All my partitions are on the same drive.

---

### Post by esc0bar on 2009-08-12
Here<s a picture of my partitinos...

---

### Post by synapsys on 2009-08-12
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You should probably re-install grub. You can re-install grub from the livecd. The fat32 partition should be mounted from fstab, after boot.

---

### Post by esc0bar on 2009-08-12
How do i reinstall grub from the cd^

I tried a few things on the CD but did not see the grub option.

---

### Post by rajeev1204 on 2009-08-12
> **esc0bar said:**
> Hey, I just got error 17 when starting up my computer.

I was running on:
Partition 1: Windows 7
Partition 2: Windows Vista
Partition 3: Ubuntu
Swap Partition

Everything was fine for a couple weeks. But, yesterday I decided to delete me Vista partition to have a FAt32 partition instead... so I could use files from this partition for both OS. Now, when I restart my computer, I get the error 17. Is there anything I can do to recuperate my seven and ubuntu partitions^

I<m currently booting from the Ubuntu CD.

Thank you.

Edit: All my partitions are on the same drive.


Hi

Since you booted from a live cd,open a terminal then type the following code:
```
sudo grub
```
```
find /boot/grub/stage1
```

Then you will get output like (hdx,y) where x is device number starting from 0 and y is number of partition where grub menu list is.FOr example hd0,4 means 4th partition of 1st hard disk.

then do the following
```
root  (hdx,y)
```

finally  ```
setup (hdx)
``` which will install grub to the device hdx

reboot.

---

### Post by host47 on 2009-08-12
Did you modify the number of partitions or the order of them?

If so, that's the problem.

You should boot with a livecd and edit your grub config with your new set-up.

---

### Post by esc0bar on 2009-08-12
Thanks a bunch, my partition now works!

---

### Post by rhchia on 2009-08-12
i have quite similar problem. but mine is "Error 12 invalid device request".
I've got windows 7, jaunty and vista on different partitions. I confirm windows 7 is working much better than vista, so i decided to delete the vista partition.
In windows 7 i had problem deleting vista partition so i login to jaunty and used gparted to delete the partition. now in the grub i faced the error 12 when i select "windows vista loader" selection. i have no problem entering jaunty. so what could be the possible solution?

---

### Post by rajeev1204 on 2009-08-12
> **rhchia said:**
> i have quite similar problem. but mine is "Error 12 invalid device request".
I've got windows 7, jaunty and vista on different partitions. I confirm windows 7 is working much better than vista, so i decided to delete the vista partition.
In windows 7 i had problem deleting vista partition so i login to jaunty and used gparted to delete the partition. now in the grub i faced the error 12 when i select "windows vista loader" selection. i have no problem entering jaunty. so what could be the possible solution?

Did you try the steps i gave in above post?

---

### Post by rhchia on 2009-08-12
> **rajeev1204 said:**
> Did you try the steps i gave in above post?
yupz. i did. guess that setup is for booting into linux which for my side is working well. except for the windows. oh and i realise its windows vista (loader) instead of windows 7. guess that's the clue. but i'm not sure what to do next

---

### Post by rajeev1204 on 2009-08-12
> **rhchia said:**
> yupz. i did. guess that setup is for booting into linux which for my side is working well. except for the windows. oh and i realise its windows vista (loader) instead of windows 7. guess that's the clue. but i'm not sure what to do next

You seem to have messed up the vista boot loader.Will probably need to use the repair cd for vista.

---

### Post by rhchia on 2009-08-13
> **rajeev1204 said:**
> You seem to have messed up the vista boot loader.Will probably need to use the repair cd for vista.

to make things worst, i followed a random thread i found online
[http://www.neowin.net/forum/lofiversion/index.php/t720866.html](http://www.neowin.net/forum/lofiversion/index.php/t720866.html)
now it load straight to windows 7. then i tried reinstall grub using the command u given. and i'm brought back to square 1 with grub loader giving window vista loader option. where is windows 7 loader then?

---

### Post by rajeev1204 on 2009-08-13
> **rhchia said:**
> to make things worst, i followed a random thread i found online
[http://www.neowin.net/forum/lofiversion/index.php/t720866.html](http://www.neowin.net/forum/lofiversion/index.php/t720866.html)
now it load straight to windows 7. then i tried reinstall grub using the command u given. and i'm brought back to square 1 with grub loader giving window vista loader option. where is windows 7 loader then?

Well,you will need to manually enter the values for windows 7 in the grub menu list.Windows 7 loader is still there probably.

Can you post the output of :

```
cat /boot/grub/menu.lst
```

---

### Post by rhchia on 2009-08-13
> **rajeev1204 said:**
> Well,you will need to manually enter the values for windows 7 in the grub menu list.Windows 7 loader is still there probably.

Can you post the output of :

```
cat /boot/grub/menu.lst
```
 
here goes...
rhchia@RH:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=9184b859-dfc0-458a-88ca-c66bf842557a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9184b859-dfc0-458a-88ca-c66bf842557a

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        9184b859-dfc0-458a-88ca-c66bf842557a
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=9184b859-dfc0-458a-88ca-c66bf842557a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        9184b859-dfc0-458a-88ca-c66bf842557a
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=9184b859-dfc0-458a-88ca-c66bf842557a ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        9184b859-dfc0-458a-88ca-c66bf842557a
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=9184b859-dfc0-458a-88ca-c66bf842557a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        9184b859-dfc0-458a-88ca-c66bf842557a
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=9184b859-dfc0-458a-88ca-c66bf842557a ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9184b859-dfc0-458a-88ca-c66bf842557a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9184b859-dfc0-458a-88ca-c66bf842557a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9184b859-dfc0-458a-88ca-c66bf842557a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9184b859-dfc0-458a-88ca-c66bf842557a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9184b859-dfc0-458a-88ca-c66bf842557a
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

rhchia@RH:~$

---

