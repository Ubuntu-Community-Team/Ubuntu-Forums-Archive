---
title: "grub2 support for usb keyboard"
date: 2009-12-28
forum: General Help
---

### Post by carisbrooke on 2009-12-28
I have viewed other instances on the forum but cant get to a solution.
I am running 9.10 + xp on an AMD based PC.

I want to ditch my old ps2 keyboard and use the new apple keyboard I am typing this on. It works fine on 9.10 and XP.
The problem is that GRUB2 cant see it so I have to use the old keyboard to do the 9.10 or xp selection.

Following he advice on similar threads I can confirm:

The bios with legacy usb support disabled cannot see the new keyboard
Grub2 with legacy usb support disabled cannot see the new keyboard

The bios with legacy usb support enabled cannot see the new keyboard
Grub2 with legacy usb support enabled cannot see the new keyboard

Grub2 with legacy usb support enabled cannot see the PS2 keyboard
Grub2 with legacy usb support enabled can see the PS2 keyboard

I have repeated this on each of the 6 usb ports I can plug into.

As a last resort I will have to buy one of those simple number-only ps2 keypads that also have arrows and an enter key to do the initial selection.

I would welcome any advice.

---

### Post by dcstar on 2009-12-28
> **carisbrooke said:**
> I have viewed other instances on the forum but cant get to a solution.
I am running 9.10 + xp on an AMD based PC.

I want to ditch my old ps2 keyboard and use the new apple keyboard I am typing this on. It works fine on 9.10 and XP.
The problem is that GRUB2 cant see it so I have to use the old keyboard to do the 9.10 or xp selection.

Following he advice on similar threads I can confirm:

The bios with legacy usb support disabled cannot see the new keyboard
Grub2 with legacy usb support disabled cannot see the new keyboard

The bios with legacy usb support enabled cannot see the new keyboard
Grub2 with legacy usb support enabled cannot see the new keyboard

Grub2 with legacy usb support enabled cannot see the PS2 keyboard
Grub2 with legacy usb support enabled can see the PS2 keyboard

I have repeated this on each of the 6 usb ports I can plug into.

As a last resort I will have to buy one of those simple number-only ps2 keypads that also have arrows and an enter key to do the initial selection.

I would welcome any advice.

Keyboard issues like that are nothing whatsoever to do with the OS or Grub, it is a limitation of old hardware/BIOS.

There is usually a BIOS option specifically addressing USB Keyboards, if you do not have one then you cannot use a USB keyboard until the OS loads.

---

### Post by carisbrooke on 2009-12-29
Your advice kept me playing with the legacy usb support on my ASUS AV8-MX motherboard. Despite the manual saying I should also have "Port 64/60 emulation" enabled for complete USB keyboard legacy support which is the default when you enable "Legacy USB Support" I tried disabling it and now GRUB2 sees it perfectly. Thanks :)

---

### Post by drs305 on 2009-12-29
This is a real leap, as I'm not familiar with Apple keyboards. But in /etc/default/grub you could try adding the first and then one of the other entries:

> 
GRUB_PRELOAD_MODULES=uhci
*and one of these...*
GRUB_TERMINAL_INPUT=at_keyboard
GRUB_TERMINAL_INPUT=usb_keyboard


Run "sudo update-grub" to incorporate the changes and let us know if it works.

Make sure you have a way to reverse these without a keyboard. ;-)

---

### Post by davemar on 2009-12-30
I'm having the same problem, and have just added those lines to /etc/...., but it hasn't made it work.

---

