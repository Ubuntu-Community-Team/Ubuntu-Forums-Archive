---
title: "Keyboard dead in GRUB"
date: 2009-07-17
forum: General Help
---

### Post by pvfjr on 2009-07-17
So when I'm booting up and I get to the Grub menu, I cannot do anthing.  The keyboard doesn't work at all, and the grub menu times out and goes to Ubuntu.  I'm trying to dual boot here, and need to get back into XP to try and export some info from Outlook.  The keyboard works fine in BIOS, Windows, and Ubuntu, but not in grub.  Any ideas?  It's just a regular microsoft USB keyboard on a desktop, nothing special.  :confused:

---

### Post by Niksko on 2009-07-17
I've had this issue before. Linux tends to sometimes not play nice with usb devices. My suggestion would be to use a PS2 keyboard if you can. Otherwise, try enabling legacy USB keyboard support in your BIOS.

-Nik

---

### Post by pvfjr on 2009-07-17
Well I feel like a dummy, you hit the nail right on the head.  I found a "Support USB Keyboard" setting in BIOS that was set to disabled.  Funny how I could use that very same keyboard in BIOS to enable the USB keyboard.  I guess that's why I figured BIOS was fine.  Anyway, it works great now.  And on to the next big issue I was originally pursuing...

---

### Post by meazz1 on 2009-07-17
> **Niksko said:**
> I've had this issue before. Linux tends to sometimes not play nice with usb devices. My suggestion would be to use a PS2 keyboard if you can. Otherwise, try enabling legacy USB keyboard support in your BIOS.

-Nik

make that another dummy.

I had the same problem and did not think the fix was that easy.

thanks

---

