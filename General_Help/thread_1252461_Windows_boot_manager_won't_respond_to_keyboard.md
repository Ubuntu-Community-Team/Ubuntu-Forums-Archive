---
title: "Windows boot manager won't respond to keyboard"
date: 2009-08-28
forum: General Help
---

### Post by insanik on 2009-08-28
Hello:

I recently installed ubuntu 9.04 on a windows vista computer through Wubi.  It worked so great that I changed the windows boot manager settings in windows to boot into Ubuntu.  now the boot manager won't respond to USB keyboard input.  I am not sure what happened.  I need to boot back into windows.  Can anybody help?

Thanks!

---

### Post by DFlame on 2009-08-28
I've had the same kind of issue before with USB keyboards. Can you try one with the "standard" connection?

---

### Post by uylug on 2009-08-28
It probably never worked. You just didn't know because Vista was the only OS on your computer. Make sense?

---

### Post by insanik on 2009-08-29
It certainly worked at one point.  I was able to select Ubuntu from this list.  If I did nothing in 6 seconds, it would boot into Windows.  I changed the default setting in Windows to boot into Ubuntu by default.

---

### Post by insanik on 2009-08-29
I don't have a PS/2 keyboard

---

### Post by DFlame on 2009-08-29
Does the keyboard function normally after Ubuntu boots up?

Can you get into the BIOS settings of your computer as it starts with this USB keyboard? This is usually done by tapping the F2, F10 or Delete key as the computer starts. It will sometimes state on screen which key to press.

If you do get into BIOS, look for and kind of "USB Legacy Support" and switch it on. Save the settings (F10 - usually) then try starting the computer again.

It might be possible to edit the boot order from within Ubuntu. I'm currently looking into this.

---

### Post by insanik on 2009-08-30
Yes, the keyboard functions properly in Ubuntu.  I have left for vacation.  I will check the BIOS setting when I return.  Thanks for your time and ideas!

---

### Post by DFlame on 2009-08-31
Have a good trip, just post here again when you're ready to carry on :)

---

### Post by insanik on 2009-09-13
DFlame, thanks for your help.  Turning on USB support in the BIOS did the trick.  Strangely, I was able to access the BIOS with a USB keyboard to enable USB keyboard support.  It's working now.  Thank you!

---

