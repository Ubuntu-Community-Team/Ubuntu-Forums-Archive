---
title: "Edit Grub. It's waaaayyy too long!"
date: 2011-04-17
forum: General Help
---

### Post by AlanInVancouverBC on 2011-04-17
I'm lost in the menu.lst file.
I've edited it before, but now I can't get a handle on it.
I've been trying different OS's over the year, lately Lubuntu. Now it's first in line (top of the order).
I'd like (until 11.04 comes out next week) Ubuntu 10.10 to be first, with a 3 second delay.
Please assist!
Here's what I've got:

```
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

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

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
# kopt=root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7802fd87-7943-49f2-99d1-6e1f8c4d5e74

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
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
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

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-25-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

:(:confused:

---

### Post by matt-fender on 2011-04-17
i use Grub-Customizer

You can get the PPA from here if you like

[Grub-Customizer]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer")

---

### Post by oldfred on 2011-04-17
That menu.lst is from grub legacy. Not sure if the new grub customizer works with grub legacy as it is for grub2.

You have copied a lot of kernels and it looks like you have copied many parts of the menu.lst over & over. You are not supposed to edit anything inside the automagic area and you should only have one start and one end of the automagic. perhaps with all the ends it is looping & adding things mutlple times?

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

Delete all but one of these.

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

If you have any custom entries make sure it is after the last (only) end.

Then run this 

sudo update-grub

Do not reboot but check that new menu.lst looks ok. If unsure repost it.
If it is not correct you may not be able to reboot. Do you have liveCD?


Why not convert to grub2? That would be the cleanest.

If you are in your install, you can do this without chrooting. See notes.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by grahammechanical on 2011-04-17
+1 and more for Grub Customizer. It is in the Ubuntu software Centre.

Regards.

---

### Post by pqwoerituytrueiwoq on 2011-04-17
How did you manage to do that?
I redid your menu.lst file
It did not appear you are dual booting so I set all the options to default
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
# kopt=root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7802fd87-7943-49f2-99d1-6e1f8c4d5e74

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
# howmany=2

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

title        Ubuntu 10.10, kernel 2.6.35-28-generic
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd        /boot/initrd.img-2.6.35-28-generic

title        Ubuntu 10.10, kernel 2.6.35-27-generic
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-27-generic

title        Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd        /boot/initrd.img-2.6.35-27-generic

title        Ubuntu 10.10, kernel 2.6.35-25-generic
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd        /boot/initrd.img-2.6.35-25-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-23-generic
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd        /boot/initrd.img-2.6.35-23-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by AlanInVancouverBC on 2011-04-17
Thanks for the fast support. I'm not rebooting yet. I'm sure I can edit this more.

OK. I think I edited the menu properly. And I installed Grub Customizer. Here's the edited menu.lst (and below that the printscreen of Grub Customizer):
```
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

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

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
# kopt=root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7802fd87-7943-49f2-99d1-6e1f8c4d5e74

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
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
# altoptions=(recovery mode) single
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

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		a7b82cd0-fb34-4723-9826-0a805a0397a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##
```

---

### Post by oldfred on 2011-04-18
If you are manually editing it, you only can have one of these.

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##
You still have many.

pqwoerituytrueiwoq has gone to a lot of effort to edit yours. But even in his I think many of the Ubuntu entries are duplicated.

It looks like the customizer creates a link in menu.lst to a grub2 grub.cfg file.

---

### Post by pqwoerituytrueiwoq on 2011-04-18
> **oldfred said:**
> pqwoerituytrueiwoq has gone to a lot of effort to edit yours. But even in his I think many of the Ubuntu entries are duplicated.
I believe I got them all
I included one of each kernel one normal boot and one recovery for each installed kernel I saw in his list
I am suprised there was no 2.6.35-26 kernel on his system

---

### Post by AlanInVancouverBC on 2011-04-24
Again, thanks for your interest and assistnace--both oldfred and pqwoerituytrueiwoq
I needed to take time away from this, this past week. Now, Saturday evening, I'm back at it.
My boot options are still the same, even tho I've greatly scaled back the menu.1st list. I'm wondering if there's another menu.1st that Ubuntu is booting from. I've installed and uninstalled Lubuntu on this and have many partitions.
Anyway, here's the updated (this evening) menu.1st. It's so much shorter, but I still get the many options on booting. I don't get the 3 second delay; it's timeless (just sits waiting for me to choose a kernel.
Alan

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
# kopt=root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7802fd87-7943-49f2-99d1-6e1f8c4d5e74

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
# howmany=2

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

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by oldfred on 2011-04-24
Are you perhaps really booting with grub2? Please be sure  to use the code tags for anything long.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by AlanInVancouverBC on 2011-04-25
Here's the script. Thanks for the idea of using this pgm.
Alan         

       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,255,944   150,255,882  83 Linux
/dev/sda2         150,256,006   156,296,384     6,040,379   5 Extended
/dev/sda5         150,256,008   156,296,384     6,040,377  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    43,034,623    43,032,576  83 Linux
/dev/sdb2          43,036,670   112,195,017    69,158,348   5 Extended
/dev/sdb5          44,994,560   112,195,017    67,200,458  83 Linux
/dev/sdb6          43,036,672    44,994,559     1,957,888  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        87bd5d51-2899-4d25-80ab-e815458569ef   ext4       Disk 2                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c71f6c87-34b2-49ec-b305-fab519b9dbb7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a245f83d-46d8-473d-adba-08c1afc51844   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        7802fd87-7943-49f2-99d1-6e1f8c4d5e74   ext4                                     
/dev/sdb6        7c56f0a7-3171-4c95-ad3a-be4447c9fc31   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a245f83d-46d8-473d-adba-08c1afc51844 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=a245f83d-46d8-473d-adba-08c1afc51844 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a245f83d-46d8-473d-adba-08c1afc51844 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=a245f83d-46d8-473d-adba-08c1afc51844 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set a245f83d-46d8-473d-adba-08c1afc51844
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro single
	initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=a245f83d-46d8-473d-adba-08c1afc51844 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=7c56f0a7-3171-4c95-ad3a-be4447c9fc31 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-22-generic
   1.0GB: boot/initrd.img-2.6.35-28-generic
   6.7GB: boot/vmlinuz-2.6.35-22-generic
   6.7GB: boot/vmlinuz-2.6.35-28-generic
   1.0GB: initrd.img
    .8GB: initrd.img.old
   6.7GB: vmlinuz
   6.7GB: vmlinuz.old

=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7802fd87-7943-49f2-99d1-6e1f8c4d5e74

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
# howmany=2

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

title		Ubuntu 10.10, kernel 2.6.35-28-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-28-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-28-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-27-generic

title		Ubuntu 10.10, kernel 2.6.35-27-generic (recovery mode)
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/vmlinuz-2.6.35-27-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro  single
initrd		/boot/initrd.img-2.6.35-27-generic

title		Chainload into GRUB 2
root		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		7802fd87-7943-49f2-99d1-6e1f8c4d5e74
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="4"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.35-28-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set 7802fd87-7943-49f2-99d1-6e1f8c4d5e74
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux_proxy ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=7802fd87-7943-49f2-99d1-6e1f8c4d5e74 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=49b20046-49c7-4916-9b14-a301134c565a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  38.3GB: boot/grub/core.img
  25.1GB: boot/grub/grub.cfg
  38.6GB: boot/grub/menu.lst
  31.2GB: boot/initrd.img-2.6.35-27-generic
  32.3GB: boot/initrd.img-2.6.35-28-generic
  38.7GB: boot/vmlinuz-2.6.35-27-generic
  38.8GB: boot/vmlinuz-2.6.35-28-generic
  32.3GB: initrd.img
  31.2GB: initrd.img.old
  38.8GB: vmlinuz
  38.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  f9 bb 38 3a 2f a5 b0 f5  2b b0 c5 f2 ba 68 e4 15  |..8:/...+....h..|
00000010  be 35 f8 5b 74 2b 3b 3e  bd ba 9f 70 83 9d 26 6e  |.5.[t+;>...p..&n|
00000020  c6 32 7d 40 df 58 63 da  e6 77 b2 3e 26 40 77 55  |.2}@.Xc..w.>&@wU|
00000030  1e a5 da e2 e6 e5 c1 2c  f7 6d 72 f7 1d 5f c6 b6  |.......,.mr.._..|
00000040  67 78 10 b0 66 3b ea b7  b1 2a bd ad 81 eb 1f 2a  |gx..f;...*.....*|
00000050  35 00 d4 00 08 2d f4 88  d8 70 1c d6 c8 4c 12 e4  |5....-...p...L..|
00000060  f5 6c 20 ac cc 37 69 dd  56 18 f0 c1 88 6d 5b c9  |.l ..7i.V....m[.|
00000070  33 f0 72 32 14 4f df 09  97 ba ed 18 7f 37 15 7c  |3.r2.O.......7.||
00000080  e6 24 30 89 41 2f 15 1e  76 a5 5e 48 d8 08 8d cf  |.$0.A/..v.^H....|
00000090  1d 8c b7 ed f4 47 25 91  96 80 f0 5b 14 7b 3d 78  |.....G%....[.{=x|
000000a0  f3 76 96 c9 e5 b6 e9 a2  53 cc 84 5c 4a fc 6e b7  |.v......S..\J.n.|
000000b0  5b 1e 73 a5 42 79 fa 42  de f8 84 ba 71 14 aa de  |[.s.By.B....q...|
000000c0  06 db 79 c2 c9 03 a9 71  01 9d dc da dc 2c 36 17  |..y....q.....,6.|
000000d0  4b d5 91 3c 16 74 5a df  62 c5 65 3a 77 c5 f2 a7  |K..<.tZ.b.e:w...|
000000e0  57 6c ef c5 21 87 43 c9  42 af cb e9 34 13 f6 b5  |Wl..!.C.B...4...|
000000f0  cc 99 50 e2 9d 38 6b 2a  cb 09 fd 33 a2 de 96 31  |..P..8k*...3...1|
00000100  3f 02 71 fd 4c 71 f4 b6  06 93 16 31 62 7e e0 ce  |?.q.Lq.....1b~..|
00000110  0d a2 7e 77 77 4c 1d 6a  1a bb 66 b8 2c f5 0e 82  |..~wwL.j..f.,...|
00000120  81 73 b8 72 9c 9a 79 6c  9e 90 bb 90 1a d5 ff aa  |.s.r..yl........|
00000130  37 5f 13 bd ec 4a ce de  8c 8a ac 40 bd b4 d7 e9  |7_...J.....@....|
00000140  91 4d ee b1 cb a1 b2 5c  24 7c 8e 67 fc 80 c8 28  |.M.....\$|.g...(|
00000150  69 3f b5 4c bc 83 00 2f  81 e7 30 ee 22 ca 0c a1  |i?.L.../..0."...|
00000160  b5 d1 34 e1 d8 37 be 76  05 10 f2 15 cb b2 91 45  |..4..7.v.......E|
00000170  bd 69 12 e6 e2 8e 0d 8f  a6 8c 96 73 f6 7b 86 8e  |.i.........s.{..|
00000180  8a dd ef 64 f2 b1 30 ed  40 2c 2d f1 db a4 15 6e  |...d..0.@,-....n|
00000190  14 f7 7d 1f 3f bb 07 71  b4 d1 9a 8f 85 db 16 de  |..}.?..q........|
000001a0  84 76 f9 f0 eb c3 b1 6c  a0 6a 81 8b af 82 8d a5  |.v.....l.j......|
000001b0  fc 17 58 a2 01 f4 90 a3  94 ba 6a 55 f4 e6 00 fe  |..X.......jU....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 39 2b 5c 00 00 00  |..........9+\...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  b8 87 37 e0 be 87 27 2a  8f 84 d5 fd 9e 3b 20 9a  |..7...'*.....; .|
00000010  92 84 1a 80 f0 e6 db 6b  f0 f9 b4 04 ea 2a ce 42  |.......k.....*.B|
00000020  1c 46 18 6e 96 0c 8d e7  c7 d5 bf 48 00 24 45 2d  |.F.n.......H.$E-|
00000030  e9 84 ad a0 b7 fa ae 5f  2b 2d 80 8b bd 94 ce 13  |......._+-......|
00000040  e4 1b b3 3c 9b d1 f2 00  00 04 31 00 01 00 1d e0  |...<......1.....|
00000050  46 00 00 02 81 56 03 40  00 35 46 20 11 a0 09 ff  |F....V.@.5F ....|
00000060  d3 5a 22 14 7e c0 03 df  02 3f 9f 44 00 00 1f 9a  |.Z".~....?.D....|
00000070  7f 49 68 40 0f 9f 5f c6  20 8b fa c8 88 bf eb 5e  |.Ih@.._. ......^|
00000080  80 2b f2 8f ce 1d 04 05  01 af f0 f6 88 8f fd 9b  |.+..............|
00000090  74 51 10 3f db 4a 08 01  fe e4 ce 22 2a fd 7c 95  |tQ.?.J....."*.|.|
000000a0  5f f0 f8 26 37 45 11 55  41 32 24 d6 3e 45 ab 7b  |_..&7E.UA2$.>E.{|
000000b0  36 f1 6e 4f 85 9a 0e 0a  e3 2b 4b 63 4e 3d 5e 60  |6.nO.....+KcN=^`|
000000c0  e3 3f 51 61 aa a2 8e fd  5d 5e 00 93 bf 1c 21 58  |.?Qa....]^....!X|
000000d0  66 15 61 4d 64 92 fb 7d  d4 a6 d0 bb 84 6b 42 60  |f.aMd..}.....kB`|
000000e0  fc a4 2c a3 a1 08 60 8b  bc 04 38 13 c2 17 62 22  |..,...`...8...b"|
000000f0  2f d1 7f 8e a8 8a 82 2a  7e 81 c0 01 ff 20 04 0f  |/......*~.... ..|
00000100  ee 03 80 07 f8 0c 1f a0  fd c6 1f e0 9c c4 54 fe  |..............T.|
00000110  e1 e7 f8 22 2b f9 f6 46  08 88 8a 7f 21 96 04 44  |..."+..F....!..D|
00000120  44 3d 90 08 88 88 ff b9  ce 11 13 ed 35 bf 01 4d  |D=..........5..M|
00000130  49 26 4a c3 ae 8d 1f d9  29 07 23 46 57 de cd d5  |I&J.....).#FW...|
00000140  74 ba 38 4d 15 28 9c b3  b5 b7 92 3c 83 40 f7 a9  |t.8M.(.....<.@..|
00000150  b1 33 43 0e 60 a4 38 5e  a3 41 6e 5c b6 cd de 9c  |.3C.`.8^.An\....|
00000160  7e c9 46 ca 7f e4 b7 3d  cb 61 b0 44 d8 69 99 b3  |~.F....=.a.D.i..|
00000170  34 55 af cb af b4 84 7f  da 82 11 0f f7 69 c3 05  |4U...........i..|
00000180  5f d5 0a be f8 54 3f db  1b 85 51 03 f5 a0 00 7f  |_....T?...Q.....|
00000190  fc 6a 9c 11 11 15 d6 eb  7d f4 23 fe 1a 81 10 f9  |.j......}.#.....|
000001a0  6f bf a2 23 f7 be 45 47  e8 9f a0 00 89 fe 10 a1  |o..#..EG........|
000001b0  15 ff 5c 90 22 af ad 13  7a 46 20 83 13 10 00 fe  |..\."...zF .....|
000001c0  ff ff 83 fe ff ff 02 e0  1d 00 ca 65 01 04 00 fe  |...........e....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 e0 1d 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200[CODE][CODE]
```[/CODE][/CODE]

---

### Post by cgroza on 2011-04-25
That is because it was not meant to be edited every day.

---

### Post by AlanInVancouverBC on 2011-04-25
inadvertently duplicated entry. Ignore.
Alan

---

### Post by oldfred on 2011-04-25
THe 80GB drive that is sda has grub2 and looks correct. The other 80GB drive has grub legacy but the partition it points to (sdb1) does not have a menu.lst. You still have a menu.lst in sdb5 but you also have grub2's grub.cfg.

So you are booting from sda into your install in sdb1. (Boot script or grub often mis-report the same drive info, it is more than likely booting sdb).

---

### Post by AlanInVancouverBC on 2011-05-07
That was in the back of my mind. But I didn't have the knowledge how to fix it, and I wasn't sure that was the problem, or that it could be solved by other means.
In the meantime, while I've learned a lot from this thread for the future, I disconnected the second drive, wiped the now ONLY drive, and booted to a 11.04 install disk.
I only use the computer for email, games and lots of surfing, so with lots of experience installing OS's getting the puter back up to my specs was easy and, as always, fun.
Thanks for your help.

---

