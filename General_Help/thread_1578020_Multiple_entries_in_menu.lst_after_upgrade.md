---
title: "Multiple entries in menu.lst after upgrade"
date: 2010-09-19
forum: General Help
---

### Post by josephe on 2010-09-19
Hi there
I know someone posted a sim. query back in 2008, but I'm know getting the same issue in Lucid. I installed the latest updates last night and when I rebooted I found I had what looks like multiple copies of the same kernel entry in the Menu.lst. I've included my file for review. Much appreciate any help sorting this out. Otherwise I reckon Lucid is rock solid. P.s I do tend to leave a lot of default entries in commented out. Will this make my boot slower at all?

Thanks

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

# title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
# uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
# kernel	/boot/vmlinuz-2.6.32-23-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro quiet splash 
# initrd		/boot/initrd.img-2.6.32-23-generic
# quiet

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7 Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

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
# kopt=root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

# title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
# uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
# kernel	/boot/vmlinuz-2.6.32-23-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro quiet splash 
# initrd		/boot/initrd.img-2.6.32-23-generic
# quiet

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
## ## End Default Options ##

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

# title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
# uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
# kernel	/boot/vmlinuz-2.6.32-23-generic root=UUID=c1e66bea-56ad-4e9b-84a3-5f54d36b63c2 ro quiet splash 
# initrd		/boot/initrd.img-2.6.32-23-generic
# quiet

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		c1e66bea-56ad-4e9b-84a3-5f54d36b63c2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by andrewthomas on 2010-09-19
Do yourself a favor and upgrade to grub2
 
[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

---

### Post by josephe on 2010-09-20
Hi there
Thanks mate, Grub2 + Update Manager + Tweak seem to do the job :-)

---

