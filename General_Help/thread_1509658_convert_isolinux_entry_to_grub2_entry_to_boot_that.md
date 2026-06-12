---
title: "convert isolinux entry to grub2 entry to boot that iso?"
date: 2010-06-14
forum: General Help
---

### Post by pythonscript on 2010-06-14
I have a live CD that I want to boot from the hard drive with grub2, but the boot loader on the live CD (in the ISO, really) is isolinux. Here's the option I want to add to my grub2 menu, using the original isolinux entry:

```

kernel vmlinuz
append vga=788 initrd=initrd.gz ramdisk_size=133551 root=/dev/ram0 rw  console=/dev/vc/4
```I want to turn this into a grub2 entry, so what would I use? The kernel is kmlinuz, and the ISO also has an initrd file called initrd.gz. I tried putting this between menuentry {} but it didn't work. 

```

loopback loop "/etc/grub.d/iso/*isofile.iso*"
linux (loop)/vmlinuz append vga=788 initrd=(loop)/initrd.gz ramdisk_size=133551 root=/dev/ram0 rw console=/dev/vc/4

```

This just hangs as soon as it loads the product's first window (so something is happening in the background with these arguments that isn't working). Thanks!

---

### Post by oldfred on 2010-06-14
These are settings I use to boot several ISO from my USB flash drive with grub2.

```
menuentry "Ubuntu 9.04 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

menuentry "Parted Magic" {
    set isofile="/boot/ISOs/pmagic-4.8.iso"

    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry " " {
set root= 
}

menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

```

---

