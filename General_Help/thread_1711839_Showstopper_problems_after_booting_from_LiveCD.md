---
title: "Showstopper problems after booting from LiveCD"
date: 2011-03-21
forum: General Help
---

### Post by vorinoch on 2011-03-21
This baffles me, and any help you guys could offer would be very much appreciated.

I have Ubuntu Lynx running in a dual-boot situation with Windows 7.  Windows was installed first, and I installed Lynx using the Alternate CD.

I had a need for a Live CD recently, so I downloaded the standard Ubuntu CD image and burned it to disc.  To check and make sure it worked, I booted off it from the machine described above.  Poked around a little, made sure it worked, and then I rebooted to get back to my standard desktop environment.  The first thing I noticed was that Windows7 was *gone* from the GRUB menu upon booting up.  This baffled me, since I hadn't done anything at all to any files when in the Live CD environment.  So, I go into Ubuntu, and notice that my wireless USB adapter (Linksys AE1000) is no longer recognized.  The only reason I can think of why this would be is that the AE1000 is a little touchy about the new kernel, and I haven't been updating it for that reason.  What I CAN'T understand is how and why the LiveCD would make changes to my bootloader and mess with my existing ubuntu installation.  Since I have no access to a wired connection, my computer is now effectively bricked until I find a solution.  Can anyone offer me any advice for how to repair the situation?  And how can I avoid this happening again?  I was under the impression that booting off a LiveCD was effectively harmless, barring user error.  And there's no way this is anything else.  Booting off that CD was the only thing I did since both Windows and Ubuntu were running flawlessly.

I'm angry, and typing this on a crappy old laptop, and want my baby back and working.

---

### Post by vorinoch on 2011-03-21
All right, I've solved the problem w/ the wireless adapter.  Running lsusb didn't return the adapter's ID, so I just unplugged and plugged it back in again.  Like magic, although I'm not certain why it happened in the first place.  Next step is to restore Windows to the boot menu.  Can anyone enlighten me as to how to do that?

---

