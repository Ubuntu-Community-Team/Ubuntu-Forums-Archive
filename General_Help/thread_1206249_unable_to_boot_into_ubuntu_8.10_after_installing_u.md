---
title: "unable to boot into ubuntu 8.10 after installing ubuntu 7.10"
date: 2009-07-06
forum: General Help
---

### Post by Brian_Newbie on 2009-07-06
I recently installed ubuntu 7.10 onto the same computer as I have Ubuntu 8.10 (previously installed). I installed 7.10 from a live CD which now is totally unsupported but allows me to log into a Government website that requires this older version of Linux.

I now want to boot into 8.10 on that computer but it only allows me to boot into the recently installed 7.10. I received the following error when I selected any of the 8.10 selections:

"error 2: bad file or directory type"
press any key to continue

When I press a key it leads me back to the OS menu and only ubuntu 7.10 will boot up. 

How can I make 8.10 boot up instead of 7.10?

P.S. The list of operating systems come up as follows: 

ubuntu 7.10 kernel 2.6.22-14-generic
ubuntu 7.10 kernel 2.6.22-14-generic (recovery mode)

Other Operating systems

ubuntu 8.10 kernel 2.6.27-14-generic (0n /dev/sda1)
ubuntu 8.10 kernel 2.6.27-14-generic (0n /dev/sda1) (recovery mode)
ubuntu 8.10 kernel 2.6.27-11 generic (on /dev/sda1)
ubuntu 8.10 kernel 2.6.27-11 generic (on /dev/sda1) (recovery mode)
ubuntu 8.10 kernel 2.6.27-9 generic (on /dev/sda1)
ubuntu 8.10 kernel 2.6.27-9 generic (on /dev/sda1) (recovery mode)
ubuntu 8.10 kernel 2.6.27-7 generic (on /dev/sda1)
ubuntu 8.10 kernel 2.6.27-7 generic (on /dev/sda1) (recovery mode)

---

### Post by danwood76 on 2009-07-07
Can you post the output of your menu.lst file please.

This from a terminal:
```

cat /etc/boot/menu.lst

```

---

### Post by Brian_Newbie on 2009-07-07
I received the following output for that command:


brianw@brianw-laptop:~$ cat /etc/boot/menu.lst
cat: /etc/boot/menu.lst: No such file or directory
brianw@brianw-laptop:~$

Note: When I installed ubuntu 7.10 from the live cd, I chose "guided" and it seemed to partition my hard drive with half the space being allotted for the newly installed 7.10 gutsy and half for ubuntu 8.10. Yet the 8.10 partition won't boot although it shows up in the list of operating systems.

---

### Post by danwood76 on 2009-07-08
Dont do that from a livecd do it from your booted 7.10.

---

### Post by RD1 on 2009-07-08
> Can you post the output of your menu.lst file please.

This from a terminal:
Code:

cat /etc/boot/menu.lst



correction ... ```
cat /boot/grub/menu.lst
```

---

### Post by danwood76 on 2009-07-08
Whoops!
Sorry mass typo there.

RD1 is correct!

---

### Post by Brian_Newbie on 2009-07-10
Been busy. Sorry for the slow reply.


That command yields the following output:

brianw@brianw-laptop:~$ cat /boot/grub/menu.lst
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
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3838a951-df34-4865-bc21-84c99cf55676 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3838a951-df34-4865-bc21-84c99cf55676 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3838a951-df34-4865-bc21-84c99cf55676 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro quiet splash 
initrd          /boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro single 
initrd          /boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro quiet splash 
initrd          /boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-11-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro single 
initrd          /boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-9-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro quiet splash 
initrd          /boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro single 
initrd          /boot/initrd.img-2.6.27-9-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro quiet splash 
initrd          /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=75fba19d-8538-42e6-bf9e-4518ad37118b ro single 
initrd          /boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu 8.10, memtest86+ (on /dev/sda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

brianw@brianw-laptop:~$

---

### Post by danwood76 on 2009-07-11
Sorry can you also ouptput the following two, need extra info to interpret it properly:
```

sudo fdisk -l
ls /boot

```

---

### Post by Brian_Newbie on 2009-07-12
Here's the output for that command:

brianw@brianw-laptop:~$ sudo fdisk -l
[sudo] password for brianw:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c02c8ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5370    43134493+  83  Linux
/dev/sda2            9368        9729     2907765    5  Extended
/dev/sda3   *        5371        9367    32105902+  83  Linux
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris
/dev/sda6            9368        9545     1429722   82  Linux swap / Solaris

Partition table entries are not in disk order
brianw@brianw-laptop:~$

---

