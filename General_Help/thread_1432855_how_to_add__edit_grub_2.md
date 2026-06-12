---
title: "how to add / edit grub 2?"
date: 2010-03-18
forum: General Help
---

### Post by shadowtroopers on 2010-03-18
Hi,
I have make partition on my hard disk during ubuntu 9.10 installation. Here are the partition details:
dev/sda1 - linux swap
dev/sda5 - ubuntu 9.10
dev/sda3 (ext3) - free space

Then I've install supergamer on my sda3 but it fails to boot. I've ask the supergamer creator about this and he gave me the lilo.conf as per below:

boot = /dev/hda
prompt
timeout = 100
bitmap=/root/.bitmap/boot.bmp
change-rules
reset
vga = 791
image = /boot/vmlinuz
initrd= /boot/initrd
root= /dev/hda1
label= linux
append="splash=silent"
read-only

How can I edit my grub 2 for this entries? The last time I've install from live dvd and update my grub 2 still it fail to boot to supergamer.

---

### Post by beastrace91 on 2010-03-18
Using the [Linux Answer Machine](http://www.google.com) I quickly found [this thread](http://ubuntuforums.org/showthread.php?t=1195275). Detailing what you are looking for.

Regards,
~Jeff

---

### Post by Brandon Williams on 2010-03-18
Assuming that you already looked at the grub2 documentation and had trouble figuring out what to do, try this ...

Use sudo to edit /etc/grub.d/40_custom. It will look like this:
```
#!/bin/sh 
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Supergamer" {
    set root=(hd0,3)
    linux /boot/vmlinuz root=/dev/sda3 ro quiet splash
    initrd /boot/initrd
}
menuentry "Supergamer (recovery)" {
    set root=(hd0,3)
    linux /boot/vmlinuz root=/dev/sda3 ro single
    initrd /boot/initrd
}
```

After making the change, run 'sudo update-grub' to apply the change to your grub config.

It's hard to know whether that is exactly right without looking at the contents of the Supergamer partition. If you still can't boot using these setting, then it would be helpful to see an listing of the files in /boot/ on the Supergamer partition.

---

### Post by shadowtroopers on 2010-03-21
Thanks Brandon, that's work perfect.

---

