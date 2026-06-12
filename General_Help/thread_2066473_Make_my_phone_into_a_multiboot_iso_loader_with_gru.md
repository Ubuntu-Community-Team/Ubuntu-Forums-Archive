---
title: "Make my phone into a multiboot iso loader with grub2"
date: 2012-10-04
forum: General Help
---

### Post by cbanakis on 2012-10-04
OK, so this project seems to be WAY over my head.

Trying to set it up, so I can plug my Galaxy S3 into a desktop, and boot to a list of iso's, where I can select, mount, and install from a selection of operating systems.

I somehow made it much farther than I expected on my own.

I formatted the phone's external sd card as fat32
Installed Grub2 on the phone.
Got it to boot to a list of iso files
And got Ubuntu 12.04 32bit And 64bit menu options working.

But none of the other iso's seem to be working.

Here is my grub.cfg
```
set timeout=30
set default=0

menuentry "Install Ubuntu 12.04 32-bit" {
 loopback loop /boot/ISOs/ubuntu-12.04-32bit.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ISOs/ubuntu-12.04-32bit.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Install Ubuntu 12.04 64-bit" {
 loopback loop /boot/ISOs/ubuntu-12.04-64bit.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ISOs/ubuntu-12.04-64bit.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Install Gnome 3.6" {
 loopback loop /boot/ISOs/GNOME-3.6.0.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ISOs/GNOME-3.6.0.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Install Tiny Core" {
 loopback loop /boot/ISOs/tinycore.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ISOs/tinycore.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Install Zorin 5.2" {
  loopback loop /boot/ISOs/zorin-os-5.2-core-32.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ISOs/zorin-os-5.2-core-32.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Install Windows 7" {
 loopback loop /boot/ISOs/Win7.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ISOs/Win7.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}
```

As I said, Ubuntu 12.04 32bit. and Ubuntu 12.04 64bit, both seem to work fine.

When I try to load Zorin, I get this.
```
Error: File Not Found
```

Everything else gives me
```
Error: File Not Found
Error: You need to load the kernel first
```


I am clearly in way over my head, but it would be so great if I could somehow get this to work.

Thanks in advance for any help.

---

### Post by sandyd on 2012-10-04
Ubuntu has "/casper/vmlinuz" inside the cd for sure. Certainly not windows 7. I believe this applies for other distros as well - you will have to provide the correct path to their /casper/vmlinuz

---

### Post by cbanakis on 2012-10-04
Thanks for your post.

What exactly is casper/vmlinuz

is that the directory for the bootloader on the iso?

---

### Post by cbanakis on 2012-10-04
Ah

I figured it out.

Found the file on all the os's except windows.

Zorin's was correct though.

Any idea how to fix that, and windows?

---

### Post by sandyd on 2012-10-05
Sorry - don't know about it. Only suspected that the other oses did not have it in the right place.
Did you check 
```
/casper/initrd.lz
```
as well?

It was possible in grub-legacy to boot windows isos. Not sure anymore about grub2, since I use use a pendrive :|

---

### Post by cbanakis on 2012-10-05
Yeah, I'm not set on using grub2
 
Its just the path I ended up on.
 
I have been trying several different methods.
 
Grub2
Yumi
Sardu
Xboot
Multisystem
 
Nothing seems to work.
 
Yumi showed a lot of promise, but still no windows?
 
It has an option for windows, and it appears to work.
 
But then when I try to boot, windows is NOT anywhere in the install menu.
 
Also, there appears to be very little documentation anywhere online that refers specifically to loading windows iso's in a multiboot usb.
 
This is becoming quite frustrating.

---

