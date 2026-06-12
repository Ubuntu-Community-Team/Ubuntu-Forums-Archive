---
title: "Partitions not showing up, need to boot into XP. GRUB: Error 12."
date: 2009-07-17
forum: General Help
---

### Post by Denji on 2009-07-17
This is kinda bad, since, well.. I need to boot into XP, and, it's creepy in general. :(

So, I install XP, ubuntu was installed first.. tried to edit GRUB, and, XP appears on the loader.. It gives me an error 12. So, I go into menu.lst, and, check over everything.. It seems to be fine, really.

It says this:

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

So I save..

And now, for some unknown reason.. ALL MY PARTITIONS REFUSE TO BE VISIBLE. I can mount them in Ubuntu, but partition editer just sees it as a giant, unallocated hard drive, which, is totally not right. >:

I can still boot into Ubuntu (thank god) but, again, partition editer refuses to see partitions, as well as many other things.

So, uh, halp a linux newb out? >:

I would also like to mention fdisk -l shows /no partitions/.

---

### Post by merlinus on 2009-07-17
Did you try

```
sudo fdisk -l
```

---

### Post by Denji on 2009-07-17
> **merlinus said:**
> Did you try

```
sudo fdisk -l
```

Mmn, okay, so that worked..

Alright, they all are there it seems. Unfortunately, gparted still thinks it's all not there. As well as a few other things. Durpdurp. >: Shall I paste the output?

---

### Post by merlinus on 2009-07-17
Yes.  Also results of

```
cat /boot/grub/menu.lst
```

---

### Post by Denji on 2009-07-17
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
timeout        30

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
# kopt=root=UUID=e25d8ef1-2c21-4473-8d36-c54736c321d9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e25d8ef1-2c21-4473-8d36-c54736c321d9

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        e25d8ef1-2c21-4473-8d36-c54736c321d9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=e25d8ef1-2c21-4473-8d36-c54736c321d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        e25d8ef1-2c21-4473-8d36-c54736c321d9
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=e25d8ef1-2c21-4473-8d36-c54736c321d9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e25d8ef1-2c21-4473-8d36-c54736c321d9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e25d8ef1-2c21-4473-8d36-c54736c321d9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e25d8ef1-2c21-4473-8d36-c54736c321d9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e25d8ef1-2c21-4473-8d36-c54736c321d9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e25d8ef1-2c21-4473-8d36-c54736c321d9
kernel        /boot/memtest86+.bin
quiet

title Windows XP
root (hd0,6)
makeactive
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

```And now for sudo fdisk -l ...

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa16060

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096   83  Linux
/dev/sda2            9328       19456    81361192+   f  W95 Ext'd (LBA)
/dev/sda3   *        9730       13717    32033610    b  W95 FAT32
/dev/sda5            9328        9729     3229002   82  Linux swap / Solaris
/dev/sda6           13718       19456    46098486    7  HPFS/NTFS

```

---

### Post by merlinus on 2009-07-17
You might try changing this

title Windows XP
root (hd0,6)
makeactive
chainloader +1 

to this

title Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1 

But the problem may well be that windows is in a logical partition, and in general does not like that.

---

### Post by Denji on 2009-07-17
> **merlinus said:**
> You might try changing this

title Windows XP
root (hd0,6)
makeactive
chainloader +1 

to this

title Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1 

But the problem may well be that windows is in a logical partition, and in general does not like that.

Alright.. I'll try that. But. One more question. D:

Why does gparted not see my partitions? Along with other various partitioning programs?

---

### Post by merlinus on 2009-07-17
Because it may be that something is not quite right with the numbering of your partitions.

What is on sda3, the fat32 partition?  Is that windows?  Or is it on sda6, which is ntfs?

---

### Post by Denji on 2009-07-17
> **merlinus said:**
> Because it may be that something is not quite right with the numbering of your partitions.

What is on sda3, the fat32 partition?  Is that windows?  Or is it on sda6, which is ntfs?

It's on sda6, sda3 is a partition with a bunch of backup data/files for when I had to reformat. (I would've loved to back up everything on DVDs, but, my DVD burner refused to work at that point. Long story.)

Oh and what you told me to change above didn't work. :C

---

### Post by merlinus on 2009-07-17
Again, the problem may well be the logical rather than primary partition.  Also, that partition (sda6) does not have a boot flag; sda3 does, but it is not your windows installation.

---

### Post by Denji on 2009-07-17
> **merlinus said:**
> Again, the problem may well be the logical rather than primary partition.  Also, that partition (sda6) does not have a boot flag; sda3 does, but it is not your windows installation.

Well, I am unsure on how to fix this then. But, thank you.

---

### Post by merlinus on 2009-07-17
So gparted is not showing any partitions?  You might try the live version:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If it sees your partitions, you can change the boot flag.

You also might try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by Denji on 2009-07-17
> **merlinus said:**
> So gparted is not showing any partitions?  You might try the live version:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If it sees your partitions, you can change the boot flag.

You also might try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

I'll try those, thank you. :3

---

### Post by canishk on 2009-07-17
I think you need to re-install the grub.

Hope you have the live cd with you.

Please follow the steps:


1. Put the Windows  installation disc in the disc drive, and then start the computer (set to boot from CD in BIOS).
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair (Vista in this case), and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Once in the command prompt, type exactly Bootrec.exe /FixMbr and then press ENTER. You will see "operation completed successfully."
8. Reboot and set BIOS to boot from the HDD again.

hope it will works

---

### Post by Denji on 2009-07-17
> **canishk said:**
> I think you need to re-install the grub.

Hope you have the live cd with you.

Please follow the steps:


1. Put the Windows  installation disc in the disc drive, and then start the computer (set to boot from CD in BIOS).
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair (Vista in this case), and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Once in the command prompt, type exactly Bootrec.exe /FixMbr and then press ENTER. You will see "operation completed successfully."
8. Reboot and set BIOS to boot from the HDD again.

hope it will works

Windows XP, not Vista.

Plus using fixmbr with Windows XP would just throw GRUB out the window, wouldn't it? Then I'd have to go into the Ubuntu live-CD, and then do all this stuff with GRUB that likely got me into this problem in the first place, because every tutorial on how to make GRUB detect XP is different. D:

I might try this if the two liveCD partitioners do not work.

Otherwise, I am going to sleep now. D: I'll check up here again in the morning when I try all this out. Wish me luck!

---

### Post by shicy on 2009-07-17
insert LiveCD of Ubuntu, open Terminal and type this:

sudo grub

find /boot/grub/stage1

then you'll get result ( something like (hd0,0) )

then type

root (hd0,0)
setup (hd0)
quit
this should work...

---

### Post by Denji on 2009-07-17
> **shicy said:**
> insert LiveCD of Ubuntu, open Terminal and type this:

sudo grub

find /boot/grub/stage1

then you'll get result ( something like (hd0,0) )

then type

root (hd0,0)
setup (hd0)
quit
this should work...

I did exactly that.

Error: 12.

---

### Post by merlinus on 2009-07-17
If grub allows you to boot into ubuntu, do not change anything!  The problem is with windows, not ubuntu!!!

---

### Post by shicy on 2009-07-17
i don't know how to help...
i'm sorry and wish you good luck

---

