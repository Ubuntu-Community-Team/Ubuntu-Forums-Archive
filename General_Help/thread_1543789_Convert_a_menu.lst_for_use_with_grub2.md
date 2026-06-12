---
title: "Convert a menu.lst for use with grub2"
date: 2010-08-01
forum: General Help
---

### Post by SilvaRizla on 2010-08-01
Hi there,

I've accidentally installed grub 2 on a BackTrack4 usb install and I need some instructions to "convert" the old menu.lst so grub2 will automatically boot BT4.  Here's the file contents:
```

# By default, boot the first entry.
default 4

# Boot automatically after 30 secs.
timeout 30

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet vga=0x317 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1 
```

Completely stumped on this one, many thanks

---

### Post by oldfred on 2010-08-01
If you have grub2 installed does not this update and find the backtrack entry?

```
sudo update-grub
```Typical entry could be like this:

menuentry "Start BackTrack FrameBuffer (1024x768)" {
    set root=(hd0,13)
        linux /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
        initrd /boot/initrd.gz
}

For grub2 with ubuntu the vga has been obsoleted so I am not sure about  that. You would have to update with the partition number using grub2  numbering not grub legacy numbering. sda1 = hd0,1 etc
Some of the other grub2 lines are optional.

---

