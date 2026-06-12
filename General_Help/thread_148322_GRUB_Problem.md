---
title: "GRUB Problem"
date: 2006-03-21
forum: General Help
---

### Post by LuisC-SM on 2006-03-21
Hi mates.

Recently I Installed FC4 on my Ubuntu Desktop and FC4 took GRUB over my booting options (If I'm not wrong, FC4 is using /boot/grub/grub.conf, while all debians use /boot/grub/menu.lst.)

I have 4 partitions; first partition is Ubuntu 5.10 Breezy, 2nd is FC4 and 3rd is empty formated in reiserfs to install Xandros or Linspire and the 4th partitition is my Linux Swap (NO MSWindoze :)).

I'd like someone to write me down th menu.lst file (completely if possible) so I can use it to Include it in the grub.conf file as far as I use a different method and did not work :(

Here is what I did before and cuold not restore my menu.lst GRUB file.

==Using the install Ubuntu disk I did the following==
After I got to the disk partition section...
1. Ctrl + Alt + F2
2. # mkdir /ubuntu
3. # fdisk -l /dev/discs/disc0/disc
4. # mount /ubuntu/ <= here I got this message.==> Can't find /ubuntu in /etc/fstab.

So I just reboot with Fedora Again and Can't fix anything :(((((

Maybe there is some workaround that I should do but I'm really tired of thinking and I have very valuable information in my Ubuntu System.

Can someone point me the right direction on what to do?

And also.. pls, be so kind to copy/paste the menu.lst file ias part of solving my problem.

Kind Regards

Luis C. Suárez

---

### Post by Sutekh on 2006-03-21
[QUOTE=LuisC-SM]

==Using the install Ubuntu disk I did the following==
After I got to the disk partition section...
1. Ctrl + Alt + F2
2. # mkdir /ubuntu
3. # fdisk -l /dev/discs/disc0/disc
**4. # mount /ubuntu/ <= here I got this message.==> Can't find /ubuntu in /etc/fstab.**
[/QUOTE]

I think you were very close, but got the 4th step wrong.  You should mount the partition that Ubuntu is on, not the folder its going to be mounted to.

Try this instead
```
mount /dev/<location of Ubuntu>
```
Just guessing, but it could be hda1.  I'm hoping you know the partition it on.

Oh yeah the menu.lst.  I don't know if this will help at all seeing as you have a particular setup.  This one is pretty much a default Ubuntu/Windows one
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
default		0

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
password --md5 $1$ZWnke0$1fzDBVjUcT1Mpdd4u/T961

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

#title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
#initrd		/boot/initrd.img-2.6.10-5-386
#savedefault
#boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

But it may help for the kernel / initrd options

---

### Post by LuisC-SM on 2006-03-21
Hi there.

Thanks so much for your help but.... it didn't work :(

I don' know what else to do.

I followed the steps and tried first /dev/hda1, later /media/hda1 etc. and nothing happened. same problem with "/etc/fstab".

Any ideas?

Kind Regards

Luis C. Suárez

---

### Post by Sutekh on 2006-03-21
[QUOTE=LuisC-SM]
I followed the steps and tried first /dev/hda1, later /media/hda1 etc. and nothing happened. same problem with "/etc/fstab".
[/QUOTE]

Sorry I just realised as I was looking over that.
```
mount /dev/hda1
```will try to mount /dev/hda1 given the info in the /etc/fstab.  

So if you say mount /dev/hda1, mount looks in the /etc/fstab for information on mounting /dev/hda1.  If there isn't the information on the mount point in the file then there will be a problem, as you got.

I meant to make a mention of this before but somehow got side-tracked.

Try
```
mount /dev/hda1 /ubuntu
```
This instead trys to mount /dev/hda1 *on* /ubuntu, which is what you are trying to achieve.

Again you should make sure that the Ubuntu partition is /dev/hda1 too.

---

### Post by LuisC-SM on 2006-03-22
Hi mate.

Tnx for your prompt reply.

Well, I gess I was close to it. I even thought of that but I was thinking in my mother (I believe :)).

Ok, I'll give it a try and will come back ASAP.

As a matter of fact, I run the LiveCD to check disk partitions (I'm writting this from the livecd), I mounted ubuntu and everything is there :)))).

so now I will try to finish reinstalling the GRUB.

BRB in some time.

Kind Regards

Luis C. Suárez

---

### Post by LuisC-SM on 2006-03-22
[QUOTE=Sutekh]Sorry I just realised as I was looking over that.
```
mount /dev/hda1
```will try to mount /dev/hda1 given the info in the /etc/fstab.  

So if you say mount /dev/hda1, mount looks in the /etc/fstab for information on mounting /dev/hda1.  If there isn't the information on the mount point in the file then there will be a problem, as you got.

I meant to make a mention of this before but somehow got side-tracked.

Try
```
mount /dev/hda1 /ubuntu
```
This instead trys to mount /dev/hda1 *on* /ubuntu, which is what you are trying to achieve.

Again you should make sure that the Ubuntu partition is /dev/hda1 too.[/QUOTE]

Hi there...

It worked like a charm :D ... So THANKS again for your time 

One last question... as I modified the boot options, my FC4 is not in the menu.lst any more, can you give me a hint on how/where to make the changes so I can also boot FC4?

Tnx in advance

Luis C. Suárez

---

### Post by Sutekh on 2006-03-22
Hey glad it worked out for you!

I'm not really sure how GRUB enu entries should look like for Fedora Core.  I guess they would be very similar to the Ubuntu ones.  

For example, perhaps you can try copy the Ubuntu one
```
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
```
And just change the **root (hd0,1)**, the **kernel /boot/vmlinuz-**, the **root=/dev/hda2** and the **initrd/boot/initrd.img-** part to match the Fedora kernel


**EDIT** - I thought I'd explain where those bold bits come from too.

 - The root (hd0,1) is the partition where the root filesystem (/) of Fedora is (in GRUB nomenclature (hd#,#))

 - The kernel /boot/vmlinuz- is the filename of the kernel image, check /boot (of the Fedora partition) to see what kernel images are there

 - The root=/dev/hda2 is the location of the Fedora root filsystem partition (device name, not GRUB name, like (hd0,1))

 - The initrd /boot/initrd.img- is the filename of the initial ramdisc, check /boot (again the fedora partition) to see the name of it

**End Edit**


If it fails don't worry just reboot back into Ubuntu and try again. 

For some more accurate advice, check out the Fedora Forums, I'm sure someone can tell you the style of the GRUB menu for Fedora.

---

### Post by LuisC-SM on 2006-03-22
Thanks again for your nice help-

Problem SOLVED.

I just went to System>Adminstration>Disks and mounted FC4.. copied the /boot/grub/grub.conf file where it says the FC4 kernel and paste it after the automagic boot in menu.lst and now I'm booting both OSs :D

Kind Regards.

---

### Post by Sutekh on 2006-03-22
How silly of me, that's *obviously* the easiest way!  In fact I do that all the time; I have multiple versions of Ubuntu running, and copy their GRUB entries over to my main partition.

#-o

---

### Post by LuisC-SM on 2006-03-22
Well Sutekh... nobody is perfect :mrgreen:

Now I will install Linspire, but I will not let it overtake the GRUB (just in case ](*,)  .

Have a nice day (or evening in case u r anywhere in America).

Luis C. Suárez

---

