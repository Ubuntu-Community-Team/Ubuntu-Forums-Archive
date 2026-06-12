---
title: "Installing Windows 7 on top of ubuntu?"
date: 2009-11-09
forum: General Help
---

### Post by Lucky75 on 2009-11-09
Hey,

I was going to install windows 7 to a second hard drive, but I already have ubuntu 9.10 installed. How would I do this? Would I:

a) Leave both drives plugged in and install 7, and then just run the karmic boot cd to reinstall grub?
b) Unplug ubuntu, install windows 7 as a stand-alone OS, and then reinstall grub?
c) Other?

Are there any foreseeable issues that I might encounter?

Thanks!

---

### Post by P4man on 2009-11-09
> **Lucky75 said:**
> Hey,

I was going to install windows 7 to a second hard drive, but I already have ubuntu 9.10 installed. How would I do this? Would I:

a) Leave both drives plugged in and install 7, and then just run the karmic boot cd to reinstall grub?

that would work, but only if you install windows on the "first" drive otherwise it wont install (or not without wiping your ubuntu partition).

> b) Unplug ubuntu, install windows 7 as a stand-alone OS, and then reinstall grub?

That would work. Its safer and has the  added benefit of being able to boot windows without the ubuntu drive and vice versa. and if grub stumbles the bios boot menu can still let you boot windows. This is my preferred way.

---

### Post by Lucky75 on 2009-11-09
> **P4man said:**
> that would work, but only if you install windows on the "first" drive otherwise it wont install (or not without wiping your ubuntu partition).



That would work. Its safer and has the  added benefit of being able to boot windows without the ubuntu drive and vice versa. and if grub stumbles the bios boot menu can still let you boot windows. This is my preferred way.

Thanks for the reply! 

So, would I just install grub to the MBR on the first disk and then set in my bios to boot the ubuntu partition first? I understand the general idea of dual booting, but some stuff still confuses me, so I apologise if I'm off base here.

---

### Post by Sef on 2009-11-09
Windows needs to be on the first primary partition.

---

### Post by P4man on 2009-11-09
> **Lucky75 said:**
> Thanks for the reply! 

So, would I just install grub to the MBR on the first disk and then set in my bios to boot the ubuntu partition first? I understand the general idea of dual booting, but some stuff still confuses me, so I apologise if I'm off base here.

I imagine you already have ubuntu installed, correct?

Lets say drive A has ubuntu on it. With grub on its MBR and the rest on /boot/grub

If you want to install windows, disconnect drive A, let windows install and install its bootloader all on drive B. When youre done reconnect drive A, set bios to boot from A, run update-grub it should find windows and add it to the grub menu

Then you can select windows and ubuntu from grub when booting drive A, and should it ever fail/crash/be removed you can still boot windows from drive B using the bios boot menu.

---

### Post by Lucky75 on 2009-11-09
> **Sef said:**
> Windows needs to be on the first primary partition.


I have two disks though, one of which is currently empty.

> **P4man said:**
> I imagine you already have ubuntu installed, correct?

Lets say drive A has ubuntu on it. With grub on its MBR and the rest on /boot/grub

If you want to install windows, disconnect drive A, let windows install and install its bootloader all on drive B. When youre done reconnect drive A, set bios to boot from A, run update-grub it should find windows and add it to the grub menu

Then you can select windows and ubuntu from grub when booting drive A, and should it ever fail/crash/be removed you can still boot windows from drive B using the bios boot menu.



Awesome. Thanks, that's what I wanted to make sure :)

---

