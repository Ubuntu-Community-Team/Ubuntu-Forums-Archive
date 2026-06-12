---
title: "USB Mouse/Keyboard lag?"
date: 2006-03-26
forum: General Help
---

### Post by iblizzard on 2006-03-26
I've got a system installed with breezy right now, a ps2 keyboard and mouse connected as well as a usb mouse and keyboard.

Everything works fine, but after a while (not sure what triggers it), the usb mouse and keyboard will start lagging.  They stay laggy until I reboot.  The ps2 mouse and keyboard are fine, and there's no other slowdown.  Any ideas what might cause this?

---

### Post by Alfdog on 2007-07-22
yeah, I'm having the same issue, does anyone have a clue as to why this is happening?

---

### Post by geraldm on 2007-07-22
I would suspect the data from the usb subsystem get delayed a very minor bit.
The drivers for PS/2 would get their data more direct, since they have no usb
subsystem overhead.  The amount of the delay should hardly be noticeable, however.

Using kernel boot option "irqpoll" will add some delay, but it is necessary for some systems if the
hardware interrupts are not well-managed.

Gerald

---

