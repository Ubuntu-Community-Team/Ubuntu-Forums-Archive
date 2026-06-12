---
title: "grub2 on usb stick - cant get it working..."
date: 2011-11-30
forum: General Help
---

### Post by justleen on 2011-11-30
Hi All,

I'm trying to get grub2 onto a usb stick without any success.

Hopefully some here can point me in the right direction....?

I've tried several guides, all to no avail. AFAIK it should be pretty straight forward..

what I have:
8gb verbatim usb stick, formatted ext3 / vfat (tried both, didn't make any difference)
ubuntu 11.10 running on my laptop
what I've done:
- checked bootable flag with cfdisk
- double checked dev with "mount"
- installed grub
```
 sudo grub-install --root-directory=/media/usb /dev/sdb 
```
-create grub.cfg 
```
 grub-mkconfig -o /media/usb/grub/grub.cfg 
```

What happens:
Trying to boot from USB gives me a "error: no such partition"
and I get dropped to a grub-rescue shell.

From there:
I can get to the menu, with finding the disk names, and setting it up by hand (all in grub rescue, ls there show me (hd0,msdos1) )
```
set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod normal
normal
```
At this stage I get the menu, and can boot an entry

What I don't get:
Apperently the prefix OR the root device is not set / not found since I'm able to boot manually from grub-rescue.

Why would the grub-install mess up the devices?
Can I manually find this somewhere in /boot/grub, so I can change the setting in order to reflect what I manually set??


Any help would be greatly appreciated!

Leen

---

### Post by efflandt on 2011-11-30
**man grub-install**

Why do some people think there is a --root-directory or --root-partition option when there is NOT (or was it different in legacy grub)?  In grub2 it is **--boot-directory**

I have had no trouble booting internal hard drive from grub2 on a USB hard drive mbr, but that was from a regular install with grub2 on the USB drive (or flash).

---

### Post by justleen on 2011-11-30
Nope, doens't matter.

(Looks like grub-install still accepts --**r**oot-directory, eventough it is not mention as such in the man-page. trying zoot or koot gives the "syntax help", boot/root don't)

Any other suggestions????


edit:
There IS a difference between the two.
--root-directory=/mnt   --> creates /mnt/boot/grub/*
--boot-directory=/mnt   --> creates /mnt/grub/*

Not that this matters, both dont fix it

---

### Post by oldfred on 2011-11-30
I have not tried installing to a flash with grub 1.99. But I have always had to manually create grub.cfg.

BIOS & grub make the boot drive hd0, on my system then each drive sda, sdb etc are in order. But if I boot sdc, it is hd0, then sda is hd1.

I did a full install to my flash from a flash. When I removed the install flash, the drive changed and there was a large gap so I think search by UUID stopped looking. I had to manually change the hd6 to hd5 and then it worked. (there was no hd3 or 4). Mutlicard readers can take a lot of USB ports that then confuse numbering.

---

