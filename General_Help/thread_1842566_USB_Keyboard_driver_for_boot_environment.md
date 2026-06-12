---
title: "USB Keyboard driver for boot environment?"
date: 2011-09-11
forum: General Help
---

### Post by joe916 on 2011-09-11
Hi everyone: i think this is a known issue but I didn't find any solution other than to use a ps/2 keyboard - I have a dual boot on an IBM compatible machine with an intel processor. Latest version of Ubuntu along with 32bit Windows XP pro (sp3). I cannot select which OS to boot because my USB keyboard will not respond until the default OS has been loaded. Its acting like there is simply no usb driver loaded.

Not sure if the keyboard driver at that point should come from the bios or from the bootloader but its coming from neither. Help?

---

### Post by joe916 on 2011-09-12
bump :)

---

### Post by joe916 on 2011-09-13
bumpity

---

### Post by -kg- on 2011-09-13
Unless you have a very old IBM compatible computer, a USB keyboard should be handled in BIOS (at least, mine are).  I have two rather old computers that I use USB keyboards on (one is a wireless, on my oldest computer in use), and I've never had a problem using them to select the desired OS from the boot menu.

How old is the computer in question?

---

### Post by dcstar on 2011-09-15
> **joe916 said:**
> Hi everyone: i think this is a known issue but I didn't find any solution other than to use a ps/2 keyboard - I have a dual boot on an IBM compatible machine with an intel processor. Latest version of Ubuntu along with 32bit Windows XP pro (sp3). I cannot select which OS to boot because my USB keyboard will not respond until the default OS has been loaded. Its acting like there is simply no usb driver loaded.

Not sure if the keyboard driver at that point should come from the bios or from the bootloader but its coming from neither. Help?

Turn on the USB Keyboard option in the BIOS.

---

### Post by joe916 on 2011-09-15
Its actually a fairly new computer..... a gigabyte motherboard with dual bios and a dual core CPU. Its interesting that you don't have the same problem: because before coming to this board I've read some discussion at another site that led me to think it was a known issue...

If you are certain that control over usb keyboard isnt handed off to the bootloader then i could update my bios I suppose. Strange thing is tho: the keyboard works fine absolutely everywhere else.... in both OS's and in the bios menu, and it works fine just any time before the screen for choosing your OS appears.

---

### Post by joe916 on 2011-09-15
dcstar - usb keyboard option is enabled in the bios

---

### Post by dcstar on 2011-09-16
> **joe916 said:**
> dcstar - usb keyboard option is enabled in the bios

Is there a "Legacy" USB option in the BIOS?

---

