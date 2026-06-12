---
title: "GRUB prevents me from booting from DVD drive"
date: 2010-12-17
forum: General Help
---

### Post by BenLi on 2010-12-17
After a stint of using Ubuntu exclusively, I'm trying to install Windows 7 again. However, when I select boot from CD/DVD in the boot menu, I just get the GRUB menu. Can anyone help?

---

### Post by tad1073 on 2010-12-17
are you saving your bios confiuration?

---

### Post by PhantmKllr on 2010-12-17
> **BenLi said:**
> After a stint of using Ubuntu exclusively, I'm trying to install Windows 7 again. However, when I select boot from CD/DVD in the boot menu, I just get the GRUB menu. Can anyone help?

There is no reason that GRUB would keep you from booting from a CD/DVD.

> **tad1073 said:**
> are you saving your bios confiuration?

Yeah, what he said.

---

### Post by karthick87 on 2010-12-17
Are you sure that you have set your CDROM to first boot device in your bios settings??

---

### Post by wilee-nilee on 2010-12-17
Use the per-session boot from menu key prompt, you may actually see it on the screen as you power on. Mine is f12 this brings up a post bios menu to choose the boot media, hd, usb, floppy, cd the usual suspects.

Look on Google with your computer model and per-session boot key, or some variation, this information probably is in the manual which is usually on the web.

---

### Post by BenLi on 2010-12-17
> **wilee-nilee said:**
> Use the per-session boot from menu key prompt, you may actually see it on the screen as you power on. Mine is f12 this brings up a post bios menu to choose the boot media, hd, usb, floppy, cd the usual suspects.

Look on Google with your computer model and per-session boot key, or some variation, this information probably is in the manual which is usually on the web.

Yes, that is exactly what I'm doing. I have the CD/DVD as my first booth device, and I can also use the per session boot setting, neither works.

EDIT: Also, I don't know what you mean by am I saving the BIOS configuration.

---

### Post by wilee-nilee on 2010-12-17
So is this a MS DVD, or a burn you made?

Have you made a pre-formatted NTFS partition for it with the boot flag as well?

Have you tried booting another cd/dvd to see if it is the disc itself, or the reader is dirty or any other possibilities.

---

### Post by BenLi on 2010-12-17
> **wilee-nilee said:**
> So is this a MS DVD, or a burn you made?

Have you made a pre-formatted NTFS partition for it with the boot flag as well?

Have you tried booting another cd/dvd to see if it is the disc itself, or the reader is dirty or any other possibilities.

It's a legitimate copy of Microsoft Windows 7 Ultimate. 

I haven't made a pre formatted partition. 

I know the disc works because I've used it before.

---

### Post by wilee-nilee on 2010-12-17
> **BenLi said:**
> It's a legitimate copy of Microsoft Windows 7 Ultimate. 

I haven't made a pre formatted partition. 

I know the disc works because I've used it before.

Do want a dual boot, if you do a install without a pre-formatted partition a NTFS with the boot flag you can wipe the Ubuntu off, or make it unallocated due to the dual partition setup that is the auto install of W7 a boot and the OS partitions.

Can you post the text from the Ubuntu terminal.
```
sudo fdisk -lu
```

**Also have you tried booting another disc as well?**

---

### Post by BenLi on 2010-12-17
I intend to use only Windows 7 on this computer, which is why I didn't bother, I was just going to reformat the entire thing. 

That's the other thing. After trying to install and boot from the disk, I can't enter ubuntu either.

What I get if I select ubuntu from the grub menu is a whole bunch of text followed by:

(initramfs)

---

### Post by BenLi on 2010-12-17
It says "mounting /dev on /root/dev failed: no such file or directory

It also can't mount /sys or /proc

"Target \filesystem doesn't have requested /sbin/init.

Might it be a harddrive problem? God knows I've had harddrive problems with this computer before...

---

### Post by wilee-nilee on 2010-12-17
If you have the Ubuntu backed up and or have nothing to loose. Boot a Ubuntu cd then open gparted right click then swap turn off, then wipe the HD clean and make a NTFS with the boot flag set what ever size you want to begin with for the main OS=C

Edit: Actually with the Ultimate version it has encryption capabilities so a wiped HD would be better the boot partition in a auto install is part of the encryption schema.

---

### Post by dcstar on 2010-12-17
> **wilee-nilee said:**
> 
.........
Have you tried booting another cd/dvd to see if it is the disc itself, or the reader is dirty or any other possibilities.

Exactly. Booting from a CD/DVD **has nothing whatsoever to do with Grub**.

The BIOS goes to the hard disk boot loader (whatever it is) after it **cannot **boot off the CD/DVD.

---

### Post by wilee-nilee on 2010-12-17
> **dcstar said:**
> Exactly. Booting from a CD/DVD **has nothing whatsoever to do with Grub**.

The BIOS goes to the hard disk boot loader (whatever it is) after it **cannot **boot off the CD/DVD.

Duh; never said it did now did I.;)

It was strange that the install a MS disc would not boot, and wiping the HD doesn't touch the mbr unless you tell it to from a command or a wiper program.

We see people all the time that can't get discs to boot even when the cd/dvd reader is first in the bios I just suggest the per-session key prompt everybody should know this anyway you don't have to go bnear the bios.

---

