---
title: "Grub2 Not Finding All OS's"
date: 2010-04-13
forum: General Help
---

### Post by SoulMazer on 2010-04-13
Hi, I am in the process of trying out different Linux distros. This is what my hard drive partitions look like:

sda1 - Ubuntu
(Free space - about 150 GB) 
sda3 - Windows (sadly)
sda4 - Windows Recovery

I successfully installed Fedora to the free space, which is now sda2, but when I was installing, I chose to keep my current bootloader so it wouldn't mess anything up. Now, I can't get Grub to detect my Fedora install, even after running 'update-grub' from the current Grub root (sda1).

How can I get Grub to detect my Fedora install?

Thanks in advance.

---

### Post by prodigy_ on 2010-04-13
Why don't you just add it manually, using **40_custom** script? Assuming that Fedora installed correctly, of course.

---

### Post by SoulMazer on 2010-04-13
I would like to, and maybe you could help me with it. I can get as far as > menuentry "Fedora 12" {
set root=(hd0,2)

} But then, I don't know what kernel/other information I need to put after that. How do I know what to put in here?

Thanks again.

---

### Post by r_s on 2010-04-13
first copy your grub.cfg file to grubBackup.cfg file and then do the changes.
fedora still uses older grub ,
 you need to add 

menuentry "fedora " {
        set root=(hd0,2)
        linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=/dev/sda3
        initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
}
 change the entries according to your system.

---

### Post by SoulMazer on 2010-04-13
Okay, well I changed my 40_custom file and now I get the error "you must load the kernel first," so I believe my kernel entry is wrong.

My 40_custom file: > #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora 12" {
set root=(hd0,2)
linux /boot/vmlinuz-2.6.31.5-127.fc12.amd64 ro root=/dev/sda2
initrd /boot/initramfs-2.6.31.5-127.fc12.amd64.img
}

Thanks again.

EDIT: Well, upon upgrading to the 10.04 beta, it auto-detected my Debian install. Problem solved.

---

### Post by r_s on 2010-04-14
try sudo blkid if you wish to know the UUID of your partition and check.

---

### Post by r_s on 2010-04-14
also you can try and do chainloading to Fedora's grub 
menuentry "fedora 12 " {
        set root=hd(0,2)
        chainloader +1
}

---

