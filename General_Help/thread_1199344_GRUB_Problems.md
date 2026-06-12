---
title: "GRUB Problems"
date: 2009-06-28
forum: General Help
---

### Post by vincent_t on 2009-06-28
I somehow screwed up my GRUB installation and then tried to fix it with instructions I found online.  That didn't work though and before I mangle things further I decided I should get some advice from someone who knows what they are doing.  Below are the details of my /boot partition:

/boot folder contents:
```
abi-2.6.28-11-generic         memtest86+.bin
abi-2.6.28-13-generic         System.map-2.6.28-11-generic
config-2.6.28-11-generic      System.map-2.6.28-13-generic
config-2.6.28-13-generic      vmcoreinfo-2.6.28-11-generic
grub                          vmcoreinfo-2.6.28-13-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
initrd.img-2.6.28-13-generic  vmlinuz-2.6.28-13-generic
lost+found

```/boot/grub folder  contents:
```
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2

```menu.lst:
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
# kopt=root=/dev/mapper/volumegroup-root ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=87c513c4-05d2-49e9-9377-18f8927e7fa8

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
uuid        87c513c4-05d2-49e9-9377-18f8927e7fa8
kernel        /vmlinuz-2.6.28-13-generic root=/dev/mapper/volumegroup-root ro quiet splash 
initrd        /initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        87c513c4-05d2-49e9-9377-18f8927e7fa8
kernel        /vmlinuz-2.6.28-13-generic root=/dev/mapper/volumegroup-root ro  single
initrd        /initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        87c513c4-05d2-49e9-9377-18f8927e7fa8
kernel        /vmlinuz-2.6.28-11-generic root=/dev/mapper/volumegroup-root ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        87c513c4-05d2-49e9-9377-18f8927e7fa8
kernel        /vmlinuz-2.6.28-11-generic root=/dev/mapper/volumegroup-root ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        87c513c4-05d2-49e9-9377-18f8927e7fa8
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```Can anyone see a problem with my setup?

---

### Post by 73ckn797 on 2009-06-28
See if this will help: [http://linuxmint.com/wiki/index.php/How_to_repair_your_grub](http://linuxmint.com/wiki/index.php/How_to_repair_your_grub)

---

### Post by vincent_t on 2009-06-28
Thank you for the suggestion.  I tried the recovery steps and it didn't work.  I double checked to see if that changed any of the info in my /boot partition or menu.lst file but they are still exactly the same.  Do you see any major differences between the contents in  your /boot folder and mine?  What about the menu.lst file?

---

### Post by egalvan on 2009-06-28
Exactly what errors are you getting?

At what point?

---

### Post by vincent_t on 2009-06-28
> **egalvan said:**
> Exactly what errors are you getting?

At what point?

Well Ubuntu is on my second hard drive (sdb) and in order to boot Ubuntu I chainload from the bootloader on the first drive (sda).  Now when I select the drive to boot from from the main bootloader it just says GRUB then hangs (well there is just a blinking cursor).  So it knows that GRUB is there in sdb1 but something must be wrong in the configuration since it just hangs.

The problem stems from the fact that when I installed Ubuntu it installed GRUB to the beginning of sda rather than sdb as I expected (I set sdb1 as bootable and mounted /boot there so I thought it would install GRUB there).  So I had to reinstall my main bootloader to sda and attempt to install GRUB onto sdb1 following various internet instructions, which haven't worked for me.

At this point I am trying to see if anyone sees a problem with my /boot partition information in post #1.  I suppose if no one has any idea what is wrong I will just have to reinstall (and obviously figure out how to get it to install GRUB to the right place this time), though I was hoping not to have to do that.

---

### Post by egalvan on 2009-06-29
> **vincent_t said:**
>  Ubuntu is on my second hard drive (sdb)
to boot Ubuntu I chainload from the bootloader on the first drive (sda). 
 Now when I select the drive to boot from from the **main bootloader **it just says GRUB then hangs (well there is just a blinking cursor).
  So it knows that GRUB is there in sdb1 but something must be wrong in the configuration since it just hangs.

**The problem stems from the fact **that when I installed Ubuntu it **installed GRUB to the beginning of sda** rather than sdb as I expected (I set sdb1 as bootable and mounted /boot there so I thought it would install GRUB there).
  So I had to reinstall **my main bootloader to sda **and attempt to install GRUB onto sdb1 following various internet instructions, which haven't worked for me.

my main bootloader to sda 
I am trying to see if anyone sees a problem with my /boot partition information in post #1.
 if no one has any idea what is wrong I will just have to reinstall (and obviously figure out how to get it to install GRUB to the right place this time), 
though I was hoping not to have to do that.


A bit confusing...
so a few questions...

What is on your first drive sda

What do you mean by **my main bootloader**

Why do you want (or need) GRUB on the second drive sdb

Why do you want (or need) to chainload from sda to sdb

Why do you state that the problem comes from installing GRUB to sda vice sdb


GRUB is a very capable and flexible boot-loader...
quite capable of handling multiple drives and multiple OS's,
it understands various file systems...
it will live on any drive, regardless of position...
it can chain-load, or be chain-loaded to...

For example,,,

you have Windows on drive one, Linux on drive two...
GRUB can live on drive one, and load either Windows or Linux.


herman's web site has a tremendous amount of information on all this... give it a visit...

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

he has info on GRUB, GRUB 2, LiLo, GAG, WinGRUB and SuperGRUB...

well worth the effort to read it all...

---

### Post by vincent_t on 2009-06-29
> **egalvan said:**
> 
Why do you state that the problem comes from installing GRUB to sda vice sdb


I guess it is only in a roundabout way that it caused the problem.  When it did that I could log into Ubuntu just fine, but it overwrote the bootloader I had in the MBR.  When I restored that bootloader into the MBR I no longer had GRUB or the rest of my /boot files anywhere on my system.  I now have the GRUB files on sdb1 by way of following various howtos.

Even if I decided to use GRUB on my first drive in the MBR I don't think I would be able to load Ubuntu because of this tidbit I found just recently:

> Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.

I am started to suspect my problem at this point is that all of those howtos assume /boot is on the root partition, but I have /boot mounted as its own partition on sdb1.  So I think the howtos are only placing the small part of GRUB that is usually on the MBR on my /boot partition but maybe not the rest of the files that are usually located in the boot folder.  Could you see if the files in your boot folder are similar to the ones in mine (mine are listed in post #1)?  Hopefully there are some that you have that are missing from mine since that would explain my problem.

---

### Post by itsjareds on 2009-06-29
So wait, your GRUB is on sda1, and Ubuntu is located on sdb1? Try changing your first entry (the first section after # # End Default Options # #) to this:

```
title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd1,0)
kernel		/vmlinuz-2.6.28-13-generic root=/dev/mapper/volumegroup-root ro quiet splash 
initrd		/initrd.img-2.6.28-13-generic
quiet
```

All that changed is that I removed the uuid (ID of a specific drive) to boot from, then added root (hd1,0), which specifies the second hard disk, first partition. Change (hd1,0) to what your specifications are.

---

### Post by mamali on 2009-06-29
do you want to recover your grub?
do this:
```
sudo grub
```
then :
```
find /boot/grub/stage1
```
it have a output put the output here:
```
root [here]
```
and at last:
```
setup (hd0)
```
```
quit
```

---

### Post by vincent_t on 2009-06-29
> **itsjareds said:**
> So wait, your GRUB is on sda1, and Ubuntu is located on sdb1? 

It **was** on sda1 (though I was erroneously expecting it to install to sdb1), but I removed it from there and was trying to get it to my /boot partition on sdb2.

---

### Post by vincent_t on 2009-06-29
> **mamali said:**
> do you want to recover your grub?
do this:
```
sudo grub
```then :
```
find /boot/grub/stage1
```it have a output put the output here:
```
root [here]
```and at last:
```
setup (hd0)
``````
quit
```

I tried that multiple times; that was the advice I found on the various howtos out there.  I don't know why that didn't work.  The files that process put onto my /boot partition appear to be the same as the ones that are there now that I just reinstalled Ubuntu and everything works perfectly now but wouldn't before the reinstall.  Go figure.

One thing I noticed was that on the alt install disk that I originally used to install my system I didn't see where to specify the GRUB installation partition so I had to use the regular install disk.

---

