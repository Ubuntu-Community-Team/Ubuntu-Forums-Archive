---
title: "Fix bootloader from LiveCD"
date: 2012-06-16
forum: General Help
---

### Post by Enigmapond on 2012-06-16
My laptop fell off a table. Not far but it fell. I tried to boot up but I have the HDD pasworded and it couldn't get past that into GRUB, just kept looping back. I dual boot Win/Ubuntu12.04. I loaded a LiveCD I had of Debian and can access all my files without any error. I was going to attempt the boot-repair-disk from the USB, (making it with netbootin). I was wondering of there was any way just to fix it from the LiveCD I already have in and when you be involved with that? Thank you in acvance!

---

### Post by carl4926 on 2012-06-16
You can chroot in to the installed system like this

```
* Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt

```

From there you can start applications as part of the installed system and fix the bootloader etc..

see also..


[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Enigmapond on 2012-06-16
Yes! Thank you that is exactly what I needed to do. All fixed now.:guitar:

---

