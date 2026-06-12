---
title: "Some settings not lasting a reboot"
date: 2010-01-22
forum: General Help
---

### Post by MrNatewood on 2010-01-22
I noticed that every time I reboot some system settings sort of roll-back automatically to some time in the past.

So far I noticed these:
-All the aMule setting. Includes connection ports and Incoming folder, very annoying.

-Firefox search box engines. every reboot the list of engines rolls back to include a lot of engines i don't want and have to remove every time. this is the only thing in Firefox that is affected, bookmarks and add-ons stick.

-Keyboard layouts. Tried clicking "apply system-wide". still rolls-back after reboot.

What could cause this? How can I set these things permanently?

I'm using ubuntu 9.10 32-bit

---

### Post by fsando on 2010-01-26
Wrt. FF: though I'm not sure it sounds like the changes you are making reside in a 'root' owned folder and not your user folder. You could try to start firefox from the command line as root and make those same changes - just to check if this is the case.

If it is indeed the case it's, IMO, not how it should be.

I have a similar problem with another app - whenever I need to upgrade or install new features I have to start it as root.

---

