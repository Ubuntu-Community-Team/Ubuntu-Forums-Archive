---
title: "How to use an iPod in VirtualBox OSE / Maverick"
date: 2011-01-17
forum: General Help
---

### Post by riprowan on 2011-01-17
I'm trying to use an iPod in a Windows 7 session running in VirtualBox OSE on Maverick.  Anyone out there doing this and, if so, how.  TIA.

---

### Post by LetsMugSanta on 2011-01-17
How far have you gotten and what issues are you having presently?

---

### Post by riprowan on 2011-01-17
I was hoping that someone out there had a working formula, but here is where I am currently at.

1. Uninstalled VirtualBox OSE and installed VBox 4.0.0 from virtualbox.org
2. Enabled USB & USB 2.0 support
3. Plugged in iPod and created a filter for the device
4. Unplugged iPod and started VM
5. Once VM was running and had focus, plugged in iPod.

RESULT

Ubuntu captured the iPod.  In the VM, the "iPod" device is greyed out.

Things I've tried to no avail:

1. Disabled / reenabled USB 2.0 support
2. Removed iPod-specific filter and created generic USB filter instead
3. Ensured that I am added to the vboxusers group
4. Disabled media auto-mounting in Nautilus
5. Read about 100 different forum queries using searches like [this]("http://www.google.com/search?q=site:virtualbox.org+ipod") and [this]("http://www.google.com/search?q=site:virtualbox.org+USB+not+mounting") none of which provide any clear working recipes to get an iPod working in VirtualBox.

I would post this question on the virtualbox forums; however, over there the advice is "Google it" or "RTFM" which, as I've shown, fails to produce a usable fix.  At least over here, people are polite.

---

### Post by riprowan on 2011-01-17
I appears that after adding myself to the vboxusers group, I needed to reboot.  Instead, I just logged off and logged back into my session.  That was insufficient.  After a full reboot, it seems to be working now.

---

### Post by PenguinSHT on 2011-04-30
Thanks a lot for your sharing. With your post, I have solved my own similar problem.

Steven

---

