---
title: "Does having a dual boot system effect how to boot into Windows Safe Mode?"
date: 2011-04-10
forum: General Help
---

### Post by RichieB07 on 2011-04-10
I have a jpeg file on my Windows system that won't delete.  However, when I try to boot into safe mode to delete it, I can not get into the menu to select "Safe Mode".  F8 just boots me right into Ubuntu.

I have Windows 7 and Ubuntu 10.10 on an Acer Aspire 5520.

Any help?  Thanks!

---

### Post by lmarmisa on 2011-04-10
I believe you have to be able to boot into Windows safe mode. But you have to press F8 after GRUB gives the control to Windows and not before.

A second comment. You could try to remove the JPG file running Ubuntu 10.10. I am sure that Ubuntu will help you to get rid of that undesired file.

---

### Post by RichieB07 on 2011-04-10
When GRUB loads, if I press F8 it automatically boots into Ubuntu (which is kind of weird, but okay).  With Windows, I'll have to try that.  I did hit F8 but it was just as the "Loading Windows" flashed up on the screen.

I actually fixed the JPEG by just renaming it from Ubuntu.  I could view it on Ubuntu but not on Windows, so I just renamed it.

Anyway, I'll give the try after GRUB allows Windows to take over and see if that works.

---

### Post by lmarmisa on 2011-04-10
My GRUB configuration defines a 5 seconds timeout and the most recent kernel of Ubuntu as default system.

When the system starts, I get a GRUB menu showing the different systems to boot, then I select Windows 7 (loader) and I hit return. Finally I press F8 several times and I get the Windows 7 Advanced Boot Options menu.

---

