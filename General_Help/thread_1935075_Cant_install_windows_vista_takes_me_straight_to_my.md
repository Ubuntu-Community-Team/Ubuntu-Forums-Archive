---
title: "Cant install windows vista takes me straight to my Ubundu 11.10"
date: 2012-03-03
forum: General Help
---

### Post by makre007 on 2012-03-03
I want to install a windows vista on my Dell vostro 1000 but when i try to boot the cd from BIOS it doesnt open, it takes me straight to my ubuntu 11.10 can some one help me install Windows vista?

---

### Post by TeoBigusGeekus on 2012-03-03
1) Is cd/dvd your first boot device in your bios?
2) Have you checked your cd/dvd on another pc to see if it really works?

---

### Post by makre007 on 2012-03-03
1.No my CD/DVD is my 3rd device boot device in my BIOS
2.Yes i just checked that.

---

### Post by TeoBigusGeekus on 2012-03-03
> **makre007 said:**
> 1.No my CD/DVD is my 3rd device boot device in my BIOS

How do you expect then to boot from a cd?
Make it the first device and try again.
Also, installing windows after you've installed ubuntu will make your grub disappear. [Here's]("https://help.ubuntu.com/community/Grub2#ChRoot") the way to get it back.

---

### Post by ajgreeny on 2012-03-03
> **makre007 said:**
> 1.No my CD/DVD is my 3rd device boot device in my BIOS
2.Yes i just checked that.
So change the CD/DVD to first priority in the boot order and try again.  You can not boot to the CD if a hard drive is still first priority device.

---

### Post by Mark Phelps on 2012-03-03
> **makre007 said:**
> I want to install a windows vista on my Dell vostro 1000
From what I recall, this is a 2007-era laptop, and a lower power one at that.  They came with XP on them, so even if you DO install Vista, if it only has the original 1GB of memory, you will likely find the performance really S...L...O...W.

>  but when i try to boot the cd 
Maybe you meant "CD" generically, but Vista didn't come on CDs, it was too big. It only came on DVDs.

And finally, BEFORE you do that install, you need to check the Dell website and confirm they offer Vista drivers for that make and model laptop.

---

### Post by efflandt on 2012-03-03
Try hitting F12 repeatedly during BIOS splash screen so the menu comes up to select boot device.  Even if you set CD/DVD to boot before hard drive in CMOS setup, many Dells still default to hard drive (or at least I have to do that to boot USB, even listed before hard drive in boot order).

Are you looking to preserve your Ubuntu or replace it?  Because if you want to keep Ubuntu on that drive you will need avoid the Windows default to format the entire drive, and also be familiar with how to reinstall grub2 to the mbr.

---

