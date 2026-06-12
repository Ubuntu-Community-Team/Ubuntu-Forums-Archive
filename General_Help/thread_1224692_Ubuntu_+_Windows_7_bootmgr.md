---
title: "Ubuntu + Windows 7 bootmgr"
date: 2009-07-27
forum: General Help
---

### Post by Toliot on 2009-07-27
Hey,
i am trying to boot win7 and ubuntu i had ubuntu previously then i installed win7 then i decided to delete ubuntu and reinstall (too many packages and i didnt know how to delete...for some reason i couldnt install anything anymore) so now i can load grub and when i choose <windows 7 (loader)> i get an error "Bootmgr missing" ctrl-alt-dlt to restart... idk what to do  any help is appreciated

btw windows 7 is installed on sda5 and i put (hd0,4) so i think that's right :P

---

### Post by lestatius on 2009-07-27
I think you need to make a seperate space for the boot loader, which I think is /boot (maybe 100mb) then have your /home  and / and virtual memory, so that when you delete ubuntu again you should be able to restart windows normally, but I'm not sure. Still new to ubuntu too.

---

### Post by merlinus on 2009-07-27
Post results of

```
cat /boot/grub/menu.lst
```

---

### Post by Toliot on 2009-07-27
> **merlinus said:**
> Post results of

```
cat /boot/grub/menu.lst
```

yes master 

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9

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
# defoptions=splash vga=795

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7b8bfbf7-c6eb-45b8-bcea-41eb2a10bff9
kernel		/boot/memtest86+.bin

title windows 7 beta (Loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by merlinus on 2009-07-27
If windows is on sda5, then try changing this

title windows 7 beta (Loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

to this

title windows 7 beta (Loader)
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

---

### Post by Toliot on 2009-07-27
Will do :)





> **merlinus said:**
> If windows is on sda5, then try changing this

title windows 7 beta (Loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

to this

title windows 7 beta (Loader)
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1


It didn't work i think what i had bfor was right cuz now it said cannt find device...?

---

### Post by merlinus on 2009-07-27
Post results of

```
sudo fdisk -l
```

---

### Post by Toliot on 2009-07-27
> **merlinus said:**
> Post results of

```
sudo fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536    5  Extended
/dev/sda3   *       27994       39536    92718080    7  HPFS/NTFS
/dev/sda5               1        6079    48829504+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

---

### Post by merlinus on 2009-07-27
What is on sdb1?  Also, if you look at sda, there are a fair number of blocks missing, from 6080 to       27993.  What is on that space?

---

### Post by Toliot on 2009-07-27
sdb is an external hd that i put all my files on (music,programs,games)
my sda is in a way that is kinda screwed up.. according to gparted (which im running off ubuntu :P not the cd) dev/sda5 is a sub of sda1 (which confuses the **** out of me) because when i click on one then the other the lines surrounding the space goes from yellow to blue. i dont really understand my harddrive atm but im certain that windows 7 is on sda3 bu there is a caution symbol beside it (not good im guessing) so im pretty much screwed right?
maybe i should run the windows 7 cd and try to fix it like that? (idk how it works anyways :P) thanks for all the help so far :) (even tho it didnt do much...i rly appreciate you trying)

---

### Post by Toliot on 2009-07-28
I'm sorry im bumping this, but i've been having a really tough time trying to fix this problem, any help is appreciated :)

---

### Post by merlinus on 2009-07-28
You can try testdisk to see if it can sort out your partition table.  Other than that, it may be best to back up important data and start afresh.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by hessiess on 2009-07-28
try using supergrubdisk to boot the partition.

---

### Post by Toliot on 2009-07-28
> **hessiess said:**
> try using supergrubdisk to boot the partition.



> **merlinus said:**
> You can try testdisk to see if it can sort out your partition table.  Other than that, it may be best to back up important data and start afresh.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


Thank you very much, i'm going to try testdisk first and see what happens and if that doesn't work ill try supergrubdisk, btw do i need to download supergrub ? or is it a default program?

---

### Post by merlinus on 2009-07-28
[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by Toliot on 2009-07-29
Ok Thanks A LOT merlinus and hessies you've been a big help,

here's how i solved the problem...
i poped in the windows 7 cd and checked for errors and i had a boot error so i told it to fix, after this i checked gparted and my sda/windows was still hd0,5 and it didn't let me boot so i decided to press e and e then changed from hd0,1 - hd0,2 and for some reason hd0,2 worked...

:) the help was much appreciated

-T0l1oT

---

