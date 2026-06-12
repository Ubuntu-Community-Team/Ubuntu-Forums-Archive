---
title: "set default kernel"
date: 2011-06-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-27
i installed a lower version kernel after a fresh install to have as a backup but it seems to be defaulting to that because when i run
```
sudo update-initramfs -u
```i get this:```

update-initramfs: Generating /boot/initrd.img-2.6.32-**31**-generic
```it should have said
```
update-initramfs: Generating /boot/initrd.img-2.6.32-**32**-generic
```[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196110&stc=1&d=1309193403[/IMG]

---

### Post by seawolf167 on 2011-06-27
You specify the kernel you want in your command, does this work for you?

```
sudo update-initramfs -u -k 2.6.32-32-generic
```

---

### Post by Joris Donders on 2011-06-27
Can't you fix that simply with startupmanager ? There you can select the default kernel in a GUI . At least that's what I understand as a solution to this problem. 

Can't think of a better one. 

Startupmanager can be installed via Synaptic.

---

### Post by drs305 on 2011-06-27
Startup Manager will work to set the default OS/kernel and is all that is really needed. An even better GUI app built for Grub 2 is "Grub Customizer". Click on the "Customizer" link in my signature line to take you to a thread explaining how to install it and what it can do.

---

### Post by pqwoerituytrueiwoq on 2011-06-27
> **seawolf167 said:**
> You specify the kernel you want in your command, does this work for you?

```
sudo update-initramfs -u -k 2.6.32-32-generic
```
that works 
it is a nice workaround

---

### Post by seawolf167 on 2011-06-27
> **pqwoerituytrueiwoq said:**
> that works 
it is a nice workaround

Glad you got it working

---

### Post by pqwoerituytrueiwoq on 2011-06-27
guess this will do i can uninstall the older kernel if i need to
better solution wanted

---

### Post by drs305 on 2011-06-27
> **pqwoerituytrueiwoq said:**
> better solution wanted

You've marked it SOLVED but it appears you may still not have what you desire.

Isn't the 'better solution' you want just to set the newer kernel as the default?

If so, we have provided 2 GUI apps that can do that. If you prefer editing the Grub2 files manually, you can click the 'Tasks' link in my signature line. Any of these methods should be able to set the latest kernel as the default when you boot.

---

### Post by pqwoerituytrueiwoq on 2011-06-27
i am using legacy grub cause grub2 hates me and it is set in grub
/boot/grub/menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        0

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a7bc74de-0ab3-48f8-a159-693f8bccb3cb

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
# defoptions=quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap

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

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-32-generic
uuid        a7bc74de-0ab3-48f8-a159-693f8bccb3cb
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap 
initrd        /boot/initrd.img-2.6.32-32-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-32-generic (recovery mode)
uuid        a7bc74de-0ab3-48f8-a159-693f8bccb3cb
kernel        /boot/vmlinuz-2.6.32-32-generic root=UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb ro  single
initrd        /boot/initrd.img-2.6.32-32-generic

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic
uuid        a7bc74de-0ab3-48f8-a159-693f8bccb3cb
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap 
initrd        /boot/initrd.img-2.6.32-31-generic
quiet

title        Ubuntu 10.04.2 LTS, kernel 2.6.32-31-generic (recovery mode)
uuid        a7bc74de-0ab3-48f8-a159-693f8bccb3cb
kernel        /boot/vmlinuz-2.6.32-31-generic root=UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb ro  single
initrd        /boot/initrd.img-2.6.32-31-generic

title        Ubuntu 10.04.2 LTS, memtest86+
uuid        a7bc74de-0ab3-48f8-a159-693f8bccb3cb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by drs305 on 2011-06-27
Your menu.lst entry shows "default 0" which would be the first menu item (2.6.32-32-generic) - so it *should* be booting the one you want.

You can check which kernel is running with the command:
```
uname -r
```

Startup-Manager works with Grub legacy. I *think* Grub Customizer will as well but can't swear to it.

---

### Post by pqwoerituytrueiwoq on 2011-06-27
```
chad@lucid-desktop:~$ uname -r
2.6.32-32-generic
chad@lucid-desktop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
chad@lucid-desktop:~$
```
as you can see it really seems to have a thing for the previous kernel

---

### Post by drs305 on 2011-06-27
Well, the good news is you are running the latest kernel.

Looking at the man page for update-initramfs, it says the "-u" updates "an existing" initramfs, so it doesn't specify it will update the latest one by release version. I don't know how it determines which one to update. 

After experimenting a bit, one guess is that it is going to update whatever the /vmlinuz shortcut points to. When I right clicked on this file and looked at the Properties, the "sudo update-initramfs -u" always updated whatever version this file pointed to. 

If it points to -31, you may be able to update /vmlinuz to -32 with:
```

sudo apt-get install --reinstall linux-image-2.6.32-32-generic
*or*
sudo apt-get install linux-image
```


At any rate, you have updated both the -31 and -32 images, and your system is booting the -32 one. If my suggestions don't pan out, perhaps someone else will enlighten us or maybe we were just not meant to understand exactly how the kernel chooses the kernel with the "-u" option.  ;-)

---

### Post by pqwoerituytrueiwoq on 2011-06-27
i have already reinstalled both via synaptic
thanks for pointing out the link thing just figured out how to fix it
vmlinuz and vmlinuz.old need to have their names inverted which i easy to do
same for initrd.img and initrd.img.old
better solution found

---

### Post by drs305 on 2011-06-27
> **pqwoerituytrueiwoq said:**
> 
thanks for pointing out the link thing just figured out how to fix it
vmlinuz and vmlinuz.old need to have their names inverted which i easy to do

:-)  Even easier if they both exist. Good thinking.

---

