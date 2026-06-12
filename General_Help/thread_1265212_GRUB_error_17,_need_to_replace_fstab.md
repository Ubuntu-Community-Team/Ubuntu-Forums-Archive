---
title: "GRUB error 17, need to replace fstab"
date: 2009-09-13
forum: General Help
---

### Post by doggie504 on 2009-09-13
currently doing this off of a live CD, im locked out of my computer. i did make a backup of fstab but i have no idea how to restore it. i tried undoing my changes to it, but i cant save it.

---

### Post by doggie504 on 2009-09-13
ugh, anyone

---

### Post by biebel on 2009-09-13
An faulty fstab can never be the cause of a grub problem afaik as fstab is not used by grub. The file you need to adjust is probably "/boot/grub/menu.lst". It sounds like grub is trying to boot from an unexisting or unreadable partition.

I had the same problem once and all I needed to do was change the jumpersetting of my ide harddisks from cable select to the right one.

---

### Post by doggie504 on 2009-09-13
well im using sata, and this was right after i edited FSTAB. all i need to do is be able to edit and save that file or replace the back up

---

### Post by biebel on 2009-09-13
Well then don't believe me.

Yes you can do what you want to do. When you're in live environment all valid partitions are shown in "Places" => "Removable Media". Figure out which one holds your ubuntu install (it will probably show as partitionsize volume) and open it. Once you have accessed it, it is mounted in /media/somename (should be the only one there)

You need superuser privileges to overwrite the fstab so you can do it from a terminal using 
sudo cp /media/somename/etc/fstabbackupfile /media/somename/etc/fstab
or launch nautilus as superuser from the terminal:
sudo nautulus
and copy it over it that way.

That being said my guess is still that you have plugged in a harddrive in a different sata port or repartitioned one and your menu.lst is now pointing to the wrong one.

---

### Post by doggie504 on 2009-09-13
ok so that did not fix it. FSTAB was the only file i did changed though what can i do to fix that menu.list?

what i did try to do was make a partition writeable

---

### Post by oldfred on 2009-09-13
Did you change partitions or edit partitions, that could renumber the partition that grub wants to boot from?

This is Herman's page on error 17 and some of the solutions with links to details.
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

If you need specific help you should download and run this bootinfo script to fully list your system configuration. Post the results.txt file it creates in the same directory it is in. You can download this while in the liveCD.
Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by biebel on 2009-09-13
from the live environment with your ubuntu partition mounted open a terminal.
```

sudo blkid

```
This will give you a list of partitions and their identifiers.
On my pc this one is the ubuntu partition:
> 
/dev/sda1: UUID="3711e9ed-19b6-416f-ae7e-6d258ebe35f8" TYPE="ext4"

Copy the uuid value without the "" (select with mouse, rightclick and choose copy)
in my case that is 3711e9ed-19b6-416f-ae7e-6d258ebe35f8
```

sudo gedit /media/somename/boot/grub/menu.lst

```
Find this entry:
> 
## default grub root device
## e.g. groot=(hd0,0)
# groot=3711e9ed-19b6-416f-ae7e-6d258ebe35f8

and paste your uuid after groot=

That should get you going again.

No guarantees that it will work for you, but don't despair if this doesn't work. I've struggled with grub (and fstab) too at times and I still have a few tricks up my sleeve :).

Good luck.

---

### Post by doggie504 on 2009-09-13
that did not work it was already set, if it helps, i dual boot vista and 9.04

---

### Post by biebel on 2009-09-13
From live **without** ubuntu partition mounted run:
```

sudo fsck -C -f /dev/sda1

```
This will check the partition for errors (Replace /dev/sda1 with whatever is aplicable to your ubuntu partition)

If errors are found there is a good chance that this will be enough.

If no errors were found please post the contents of the following files (from your ubuntu partition not the livecd):
/boot/grub/menu.lst
/boot/grub/device.map
and the output of
```
sudo blkid
```

I won't be able to post again until tomorrow, but in the meantime this might help and it won't do any harm:

Mount your ubuntu partition in live envirionment (has to be the jaunty cd otherwise you won't be able to boot from ext4 partitions)
```

sudo grub-install /dev/sda --root-directory=/media/somename --recheck

```
That is assuming your ubuntu and grub are on sda
This reinstalls grub

---

### Post by doggie504 on 2009-09-13
MENU.LST
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
# kopt=root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=50978d98-afe7-4dcd-b547-17685283113d

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
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        50978d98-afe7-4dcd-b547-17685283113d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=50978d98-afe7-4dcd-b547-17685283113d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        50978d98-afe7-4dcd-b547-17685283113d
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

```Device.map
```
(hd0)    /dev/sda
```Output of Sudo Blkid
```
/dev/sda1: UUID="9E7E0C797E0C4C89" TYPE="ntfs" 
/dev/sda5: UUID="50978d98-afe7-4dcd-b547-17685283113d" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="afea120d-8c1f-4d16-afdc-b24a1c7f8432" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="357c53f4-da0e-48c6-b226-a6d3d986d549" TYPE="swap" 
/dev/sda7: UUID="6368746f-2074-616b-6f65-207575696400" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="5288BC3988BC1E03" LABEL="Shawn" TYPE="ntfs" 

```

---

### Post by doggie504 on 2009-09-13
well re-installing grub worked!! thanks for you're help though.

---

### Post by sgosnell on 2009-09-13
Follow the instructions here:

[Reinstall GRUB using the live CD]("http://www.thelinuxsociety.org.uk/content/reinstall-grub-using-live-cd").

---

### Post by oldfred on 2009-09-13
Which drive boots first? Did you change boot order in BIOS?

Did you run the filecheck on your ext2 partitions (fsck)?

The bootinfoscript.sh gives all the info you posted so far plus some additional info to help diagnose your system. i.e. what is in MBR and what partitions have grub, windows and ubuntu with versions.

Lacking bootinfoscript give us also 

```
sudo fdisk -l
```

---

### Post by biebel on 2009-09-13
Glad it works again =-)

---

### Post by doggie504 on 2009-09-13
forgot, going to set as resolved. i just re-installed GRUB.

---

