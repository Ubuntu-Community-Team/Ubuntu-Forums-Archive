---
title: "stuck with grub"
date: 2010-01-15
forum: General Help
---

### Post by deathseek on 2010-01-15
cant boot kubuntu stuck with grub cant see anything but grub... help fast

newbie dying:(

---

### Post by Jackzor on 2010-01-16
> **deathseek said:**
> cant boot kubuntu stuck with grub cant see anything but grub... help fast

newbie dying:(

What does grub say?

---

### Post by deathseek on 2010-01-16
it looks like a console for grub... it has [COLOR=Red]**sh:grub>**[/COLOR]

---

### Post by deathseek on 2010-01-16
ls
set prefix=(hd0,6) /boot/grub
set root=(loop0)
ls /boot
insmod /boot/grub/linux.mod
linux /vmlinuz root=dev/sdXY loop= /ubuntu/disk root.dok.ro
initrd /initrd.img
boot

after that it tried to load then...

iv done this steps it tried to load kubuntu but it gives me the msg kernel panic - syncing: VFS : unable to mount foot fs on unknown-block (0,0)

---

### Post by killercow84 on 2010-01-16
You can try to boot the live cd of ubuntu/kubuntu or something and reinstall grub with the following tutorial:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

good luck ;)

---

### Post by deathseek on 2010-01-16
i wish i could but i dont own a usb....if thats the last step to boot kubuntu im gonna do that... thanks for the post

---

