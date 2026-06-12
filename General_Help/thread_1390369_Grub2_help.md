---
title: "Grub2 help"
date: 2010-01-25
forum: General Help
---

### Post by dbzkid on 2010-01-25
I have installed grub2 onto my usb drive while i have been able to boot ubuntu 9.10 I have tried DSL and Backtrack and neither want to boot (I may want to switch back to grub legacy). Either way I point the grub.cfg to the linux kernel and the initrd but to no avail It seems like it is loading but doesn;t. For dsl it wont go past the kernel loading and initrd (two lines show up on the top of the screen but I don't remember what they say will post later) then it just reboots and the bios shows up again. for back track It seems like it booted correctly but then goes in to a minimal terminal after loading some items (I will also post what it says in a little while) I don't know if these are bugs or if im doing something wrong but I'll post my grub.cfg

```
menuentry "ubuntu 9.10" {
    set isofile="/boot/iso/ubuntu.iso"
    loopback loop $isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "dsl" {
    linux /boot/isolinux/linux24 fromhd=/dev/hda1
    initrd /boot/isolinux/minirt24.gz
}

menuentry "BackTrack 4" {
    set isofile="/boot/iso/bt4-final.iso"
    loopback loop $isofile
     linux (loop)/boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
    initrd (loop)/boot/initrd.gz
}

```

As you can see I have tried a cheat code for dsl tha tells it to boot from the first hd (which should be the usb drive because grub is booting off of that) and it wont boot off of that if i insert no cheat code it gives me the same result. I am booting Live Disks from the usb (on the ubuntu entry I am booting the actual iso).

Please Anyone help
Thanks,
Kevin

---

