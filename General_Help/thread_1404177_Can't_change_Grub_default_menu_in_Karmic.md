---
title: "Can't change Grub default menu in Karmic"
date: 2010-02-11
forum: General Help
---

### Post by marcove64 on 2010-02-11
Hello,

Althought /etc/default/grub has GRUB_DEFAULT=6, after grub-update
nothing changes and the default menu entry is still the first.
Can someone tell me how to change the Grub default menu entry?
Thanks a lot.
Bye, Marco.

---

### Post by NightwishFan on 2010-02-11
Run this command then reboot:
```
sudo update-grub
```

Just did this 5 minutes before posting to set RT kernel as the default. ;)

---

### Post by marcove64 on 2010-02-11
Thanks a lot for your answer.
I did this:

```

root@marco-desktop:~# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```and nothing changes.
There is no mention to /etc/default/grub that is the
file that holds the correct parameters.
This is my /boot/grub/menu.lst:

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
default saved

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
# kopt=root=UUID=e909b021-f0b8-4a11-80e5-a92703d8ce43 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e909b021-f0b8-4a11-80e5-a92703d8ce43

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=e909b021-f0b8-4a11-80e5-a92703d8ce43 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=e909b021-f0b8-4a11-80e5-a92703d8ce43 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=e909b021-f0b8-4a11-80e5-a92703d8ce43 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=e909b021-f0b8-4a11-80e5-a92703d8ce43 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e909b021-f0b8-4a11-80e5-a92703d8ce43 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e909b021-f0b8-4a11-80e5-a92703d8ce43 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        e909b021-f0b8-4a11-80e5-a92703d8ce43
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Do you think that I have to modify this
directly and how?

---

### Post by NightwishFan on 2010-02-11
If you are using GRUB2, the file should not be menu.lst, but grub.cfg that you are not supposed to edit. Is that left over from a previous update?

---

### Post by Oceola on 2010-02-11
Same issue with me but I found probably the worst possible way to fix things. I dual boot Karmic 9.10 and Hardy 8.04. When I updated the kernel for Hardy 8.04 today there was no apparent easily editable menu.lst for me to add the updated kernel information from the grub on the 8.04 disc to the 9.10 disc.
I have two hard drives and the menu.lst before the update to Karmic (Hardy had been on both drives but as separate operating systems)was relatively easy using mount to load the opposite hard drive and sudo gedit to perform the editing. I got around it installing the plain Grub from the 9.10 repository which removed the Grub-PC . During this process it asked if I wanted to remove the configuration files, I agreed and it then warned me of leaving the machine in an unbootable condition. I then reinstalled the same plain Grub. It did not pick up on the new version of the 8.04 system so I re-installed the Grub-PC. When i did this it provided me with a prompt asking if the Linux command lines looked OK. Nothing was visible after the prompt and I believe it was looking for the "kopt" information. However I hit enter and the prompt came up again, nothing visible I hit the prompt again and it asked which devices I wanted to place in the boot menu. It provided the options /dev/sda1 or /dev/sdb1 or both. In my case I added both seperated by a space example: /dev/sda1 /dev/sdb1. When I rebooted the machine the new version of the 8.04 kernel showed in the Karmic run menu list. It's just a guess here but it could be as simple as a re-install of Grub-PC without all the back and forth I went through unless there is a simple file which can have the updated information from the opposite kernel added. The primary kernel (9.10) should always address this during an update and displayed in the dumb terminal in Synaptic. Going the other way from the older version to the newer is where the issue lay.

This was all done by accident so be very careful.

---

### Post by marcove64 on 2010-02-16
> **NightwishFan said:**
> If you are using GRUB2, the file should not be menu.lst, but grub.cfg that you are not supposed to edit. Is that left over from a previous update?


I installed Karmic from scratch, so the installation process 
installed what now I have.
I had a look and I have either menu.lst and grub.cfg in /boot/grub.
In grub.cfg, that is not supposed to be edited I still have this:

```

set default="0"

```even if in /etc/default/grub I have:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=6

```
So, why running update-grub, does not change anything in
/boot/grub/grub.cfg ?
This is my question!
Any clue?

---

### Post by marcove64 on 2010-02-16
```

#sudo apt-get install grub-pc

```

solved the problem. This is the correct fix
form my problem. Now update-grub updates
/boot/grub/grub.cfg

Thanks a lot!
Bye

---

