---
title: "new kernel oddness"
date: 2006-02-24
forum: General Help
---

### Post by MrCheese on 2006-02-24
Hi, I am stuck running kernel 2.6.12-8-386 as if I try to upgrade I'm left with a duff boot - all goes ok until I get error messages relating to drive geometry, finally clagging out with "Target filesystem doesn't have /sbin/init".

I have a pci IDE-Raid card with two drives (/dev/hda (data) & /dev/hdc (test installs)) hanging off it, my internal hdds are /dev/hda (XP) & /dev/hdf (Ubuntu). I guess that the kernel is getting confused loading the SiL raid card driver & hitting the wrong hdd. I use lilo the conf has a BIOS section which remaps the hdds as below :    

```
# WARNING: do not forget to run lilo after modifying this file

boot=/dev/hdf
map=/boot/map
default="windows"

# Bitmap configuration for /boot/coffee.bmp
bitmap=/boot/coffee.bmp
bmp-colors=12,,11,15,,8
bmp-table=385p,100p,1,10
bmp-timer=38,2,13,1

install=bmp
prompt
nowarn
timeout=50

menu-scheme=wb:bw:wb:bw
disk=/dev/hdf bios=0x80
disk=/dev/hde bios=0x81
disk=/dev/hda bios=0x82
disk=/dev/hdc bios=0x83

other=/dev/hde1
	label="windows"
	table=/dev/hde
	map-drive=0x80
	   to=0x81
	map-drive=0x81
	   to=0x80

image=/boot/vmlinuz-2.6.12-8-386
	label=linux
	root=/dev/hdf5
	initrd=/boot/initrd.img-2.6.12-8-386
	append="noapic devfs=nomount splash=silent acpi=ht"
	read-only
	vga=normal

image=/boot/vmlinuz-2.6.12-10-k7
	label=Linux-K7
	root=/dev/hdf5
	initrd=/boot/initrd.img-2.6.12-10-k7
	append="noapic devfs=nomount splash=silent acpi=ht"
	read-only
            vga=normal

```

Can anyone shed light on this oddness as I'd really like to upgrade to a later kernel & compile stuff to fit!

---

