---
title: "cant boot off of live usb"
date: 2011-08-14
forum: General Help
---

### Post by ionbasa on 2011-08-14
Hello, I am having issues booting a live usb drive. The 8gb drive is partitioned to fat32 and has grub 2 installed under /boot/grub
my iso images are located under /boot/iso
Now I am having an issue booting the 11.10 nightly .iso
my grub.cfg looks like this:
```
set timeout=10
set default=0

menuentry "Ubuntu 11.10 x64 Live ISO" {
    set isofile="/boot/iso/oneiric-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile --
    initrd (loop)/casper/initrd.lz
}

```

When booting from the usb stick I can see the grub entry, but after selecting it and hitting "Enter" it just blinks an _ (aka underscore) in the upper left corner of my screen, then nothing happens any thoughts?:confused:

---

### Post by Foxheadz on 2011-08-14
You can't boot of a usb like a hardrive you have to create a live usb using something like unetbootin, and then set your BIOS to boot from the usb.

Link for unetootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by ionbasa on 2011-08-14
> **Foxheadz said:**
> You can't boot of a usb like a hardrive you have to create a live usb using something like unetbootin, and then set your BIOS to boot from the usb.

Link for unetootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/)
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
This says I can, I just have grub 2 installed on the usb, all i want to do is boot the live .iso of the nightly which doesn't work with either tutorials.

---

### Post by Foxheadz on 2011-08-14
I would recommend just burning the iso to the usb with unetbootin, have you tried that?

---

### Post by ionbasa on 2011-08-14
> **Foxheadz said:**
> I would recommend just burning the iso to the usb with unetbootin, have you tried that?
yes, it works with unetbootin, but I wanted to add the 11.10 to my flash drive, as i have partedmagic, memtest86+, and fedora, which all boot fine, its just the nightly that wont work.

---

### Post by Foxheadz on 2011-08-14
I see, well if you have a windows computer you can try using xboot to easily put multiple iso on one bootable usb [https://sites.google.com/site/shamurxboot/](https://sites.google.com/site/shamurxboot/)

---

### Post by ionbasa on 2011-08-14
> **Foxheadz said:**
> I see, well if you have a windows computer you can try using xboot to easily put multiple iso on one bootable usb [https://sites.google.com/site/shamurxboot/](https://sites.google.com/site/shamurxboot/)
It works! Thank you.

---

### Post by Foxheadz on 2011-08-14
No problemo, it's what im here for

---

