---
title: "installed L as dualboot with Ubuntu. Lost Ubuntu"
date: 2011-04-03
forum: General Help
---

### Post by AlanInVancouverBC on 2011-04-03
Lubuntu doesn't appear to have incorporated my Ubuntu boots into the splash screen (Is that where I can choose which kernel to boot to?). The screen shows only 2 Lubuntu kernels.
BTW, I installed Lubuntu because it's lean, and on my 2Ghz machine I thought it'd be better than Ubuntu. But it's just "anorexicly" lean.
:(
Here's my Menu.1st:

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

---

### Post by AlanInVancouverBC on 2011-04-03
I fixed it.
Scanning through other posts on other related issues, I found that I don't use menu.1st anymore. Using some terminal commands to install a file and using that file to update the grub, I got it.
Thanks to whomever that was.

---

