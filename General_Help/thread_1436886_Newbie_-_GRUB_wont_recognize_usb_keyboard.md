---
title: "Newbie - GRUB wont recognize usb keyboard"
date: 2010-03-23
forum: General Help
---

### Post by cuzzinit17 on 2010-03-23
It worked fine for awhile, but recently my usb keyboard wont work, ONLY IN GRUB. So I cant use grub to select another boot option. This kbd does work in Ununtu and on my other XP machine. Old version of Grub, I believe. (not GRUB 2). No error messages displayed.
 
 
Dave

---

### Post by coffeecat on 2010-03-23
This is a BIOS problem - irritatingly common too.

Use whatever magic key your motherboard needs to get into the BIOS at the POST screen. Then have a look for an option to enable USB keyboard support. Sometimes this appears (somewhat unintuitively) as legacy USB support. Of course, you'll need a PS2 keyboard to be able to get into the BIOS, because the BIOS won't detect the USB keyboard until you've enabled USB keyboard support. (You really have to wonder what BIOS programmers are smoking. :rolleyes: )

The reason that the keyboard works fine in Ubuntu and Windows is that both OSs have their own drivers to detect USB keyboards. Grub relies on the BIOS. No BIOS detection of the keyboard = won't work in grub.

---

### Post by cuzzinit17 on 2010-03-23
Thanks coffecat- I'lll give that a try in a few minutes and let you know if it works. I'm using an HP xw6000 - they do have that exact "legacy usb support" so I will check it. If thats the problem its weird that it would change by itself.
 
Dave
 
> **coffeecat said:**
> This is a BIOS problem - irritatingly common too.
 
Use whatever magic key your motherboard needs to get into the BIOS at the POST screen. Then have a look for an option to enable USB keyboard support. Sometimes this appears (somewhat unintuitively) as legacy USB support. Of course, you'll need a PS2 keyboard to be able to get into the BIOS, because the BIOS won't detect the USB keyboard until you've enabled USB keyboard support. (You really have to wonder what BIOS programmers are smoking. :rolleyes: )
 
The reason that the keyboard works fine in Ubuntu and Windows is that both OSs have their own drivers to detect USB keyboards. Grub relies on the BIOS. No BIOS detection of the keyboard = won't work in grub.

---

