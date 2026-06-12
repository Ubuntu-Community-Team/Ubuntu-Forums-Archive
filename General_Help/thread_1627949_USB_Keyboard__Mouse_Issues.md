---
title: "USB Keyboard / Mouse Issues"
date: 2010-11-22
forum: General Help
---

### Post by DigitalNoise on 2010-11-22
Just installed 10.10 over an old 8.10 install - I formatted the partition before installing.

For whatever reason, neither my USB keyboard or Mouse will work when I boot into 10.10.  The keyboard works fine at the GRUB menu; and both the keyboard and mouse work just fine on the Live CD - but not when booting from disk.

And the best part is - both the Keyboard and mouse worked just fine under 8.04.

So, I'm at a loss - I've tried the recovery mode and I didn't spot any error messages.  It's just like it won't initialize the USB system at all.

---

### Post by TeoBigusGeekus on 2010-11-22
Try enabling usb legacy support from bios.

---

### Post by DigitalNoise on 2010-11-22
> **TeoBigusGeekus said:**
> Try enabling usb legacy support from bios.

That's already enabled - I originally tried it without, but then the keyboard wouldn't work at the GRUB menu.

It seems something in 10.10 is shutting down the USB ports - I say that, because my lighted keyboard goes dark once I'm at the login screen; yet it's lit when at the GRUB menu and works just fine there, as well as when booting into the Live CD.

---

### Post by DigitalNoise on 2010-11-23
Anyone have any ideas?  This is aggravating, and there doesn't appear to be any reason for this issue - the Live CD works just fine, and the 8.10 distro worked fine with the same exact keyboard and mouse.

---

### Post by JustGeorge on 2010-11-28
After new installation USB keyboard didn't work for me (it did work on Live CD) so I couldn't log in as I couldn't type the password.

Anyway I disabled "USB 2,0" support in Bios and then keyboard worked.

---

### Post by DigitalNoise on 2010-11-28
> **JustGeorge said:**
> After new installation USB keyboard didn't work for me (it did work on Live CD) so I couldn't log in as I couldn't type the password.

Anyway I disabled "USB 2,0" support in Bios and then keyboard worked.

Did your mouse work without a problem?

My BIOS is currently set to support both 2.0 and 1.1 on the USB ports; I'd really rather not force it down to 1.1 only, as that will severely hamper the performance of my external HDD.

And frankly, 10.10 should support USB 2.0 - especially if it's working on the Live CD - that's whats driving me nuts over this.

---

### Post by JustGeorge on 2010-12-02
> **DigitalNoise said:**
> Did your mouse work without a problem?
Yes. I actually found out I needed to do something else to make it work.

It is kinda weird, but this works for me:

Shutdown.
Unplug computer from the power.
Try to start computer with the power button.
Plug it back in and start the computer.

USB Keyboard works now. :)

---

