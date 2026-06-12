---
title: "Booting from disk not in BIOS"
date: 2009-07-28
forum: General Help
---

### Post by lagbot7000 on 2009-07-28
I'm attempting to dual boot Ubuntu and Windows 7 RC1, but I've run into a stopping point. Windows is installed to a SCSI disk which is not visible in BIOS (The int13 function of my SCSI card must be disabled for the Intel raid to be visible, which contains my mass storage raid). I have Ubuntu booting from a USB stick which I am using as a startup key, since there is no bootable OS without it.

So I've gotten to the point where I am trying to configure Grub to boot into my Win7 disk, but since it is not visible to the BIOS at boot, it isn't visible in Grub. I simply receive a "disk not found" error when I try to select the Win7 boot option in Grub.

My question is whether it is possible to boot from a disk not visible in BIOS via Grub? Or if not Grub, is there an alternative bootloader I can use to boot into my Windows 7 disk?

---

### Post by munky99999 on 2009-07-28
> My question is whether it is possible to boot from a disk not visible in BIOS via Grub?
Not sure. I swear I've done this before. With lilo or grub. I do believe it's done with delays basically. 

Grub 2.0 I believe has this capability in a much more easy design.
[http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

I have no idea though.

> Or if not Grub, is there an alternative bootloader I can use to boot into my Windows 7 disk? 
It certainly wont be easy.

In essence you want to load something that the computer cant see. So you will need something that can be seen. If USB key is all you can do. Then that's what you use.

My bet would be to try grub2.

---

