---
title: "Randomly the boot fails"
date: 2010-06-10
forum: General Help
---

### Post by a_marcone on 2010-06-10
Hi there,
I'm having a problem with my boot.
I copied with clonezilla an installation of ubuntu to other clients with identical hardware (same motherboard, same monitor, same anything).
Everything works fine, but just sometimes (rarely, but it happens) the boot won't load the system.
This is what it freezes on:

> Booting Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic

root (hd0,0)
  Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.24-27-generic root=UUID.....
e404f9b ro quiet splash
    [Linux-bzImage, setup=0x2a00, size=0x1d3b98]
intrd /boot/intrd.img-2.6.24-27-generic
    [Linux-intrd @ 0x1f8cd000, 0x7225a2 bytes]


then it stops.
Normally the system holds there for like a second and then it gives the message:

> Loading, please wait...

and everything gets started.

But as I said, in some cases, it would just stop there, and it doesn't even let you poweroff the computer.
I myself blame clonezilla for this sort of errors I get.. but, is there a way to fix this?

Thanks in advance

---

### Post by arrange on 2010-06-10
You could try rebuilding the *initrd* image```
sudo update-initramfs -u
```(I hope the command is the same for 8.04)

Also check your RAM (choose *memory test* in the Grub menu).

---

### Post by a_marcone on 2010-06-10
I will definetely try that. Not sure when I'll know whether it worked or not tho :D Thanks!

---

### Post by a_marcone on 2010-06-22
bump - nope, that didn't make the trick.
It still keeps giving me that. Any other ideas?

---

### Post by a_marcone on 2010-07-12
This is what we tried:
- Upgraded Grub.
- removed the UUID from the boot.
No success.

- Re-installed the whole OS with the kernel 2.6.24-28, everything worked perfectly. Rebooted for about 1100 times before it crashed for other reasons (imho quite a good percentage)
- Moved the hdd from the original hardware to another kiosk with the same identical hardware, but after like 20 reboots, same thing..freeze on the startup part, like posted above. (Thus we excluded clonezilla).

- Upgraded the Bios, still testing it, we'll see if anything changes.

---

