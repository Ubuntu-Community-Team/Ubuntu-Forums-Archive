---
title: "can't boot, need to manually setup grub entries"
date: 2009-12-16
forum: General Help
---

### Post by alanwalterthomas on 2009-12-16
I just installed Fedora 12 to experiment with a little alongside my main existing Ubuntu install, with boot on /dev/sda3. I didn't install the bootloader because I didn't want to mess around with something that could affect my existing Ubuntu install. I've been trying to get Fedora 12 to boot but I can't figure out how to properly set up grub2. os-prober didn't detect it so I put the following 

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Fedora-12_x86_64" {
        set root=(hd0,3)
        linux /vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=e5ffae75-73d3-4d9c-a257-dbf1ae56e3c1 ro quiet splash
        initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
}

in /etc/grub.d/40_custom (of my ubuntu install) & ran update-grub2. When I choose Fedora in the grub2 menu I get as far as seeing the graphical progress meter on the splash screen go partway, then the screen goes black & I see about 30 messages saying 
mount: /dev/sda3 already mounted or /sysroot busy
mount: according to mtab /dev/sda3 is already mounted on /sysroot
At the end it says 
Boot has failed, sleeping forever. 
What did I get wrong in my /etc/grub.d/40_custom file?
(by the way, I originally thought I should have /boot/vmlinz... , /boot/initramfs... but that gave file not found errors. Getting rid of "boot/" at least got me partway)

---

### Post by john newbuntu on 2009-12-17
Covered in: [http://ubuntuforums.org/showthread.php?p=8431584](http://ubuntuforums.org/showthread.php?p=8431584)

---

