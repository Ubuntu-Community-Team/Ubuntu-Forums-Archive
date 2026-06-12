---
title: "I need a guide, a guide to tell me how to move in bootscreen (laptop screen is broken"
date: 2010-09-01
forum: General Help
---

### Post by Nintendofanthr33 on 2010-09-01
Thank you for reading this

Recently I installed ubuntu with Wubi.
I had a fine install with 10.04 desktop 32bit. 
Since I am unable to see the boot screen, I kept loading to windows
So. I switched the autoboot to option on windows in (controlpanel/system/advancedsystemoptions/boot) and swiched it to ubuntu.
Ubutntu works fine on my external monitor. 
After the second session,, I installed a restricted driver (nvidia) and installed all updates needed.
I reboot. next thing, ubuntu won't show on my external monitor. I know it's plugged in correctly, swell as using the FN button.
I'm getting paranoid because, I am unable to see the boot menu, so I cannot tell if I'm pressing the right buttons to get to windows and ubuntu.
I cannot tell what happens if I press F8 or ESC.

I need someone who can tell me the buttons to press EXACTLY so I can go into rescue mode. Or atleast windows and reinstall ubuntu. (I'd prefer rescue mode)  (FYI, I'm on my iPhone at the moment.)

I can hear the boot sound when ubuntu loads.

---

### Post by bcbc on 2010-09-01
Try this [http://support.microsoft.com/kb/927391](http://support.microsoft.com/kb/927391) to rebuild the BCD store.

Never default to a wubi ubuntu install from the windows boot manager without a timeout. If the wubi root.disk corrupts or you have problems like you encountered, then you're stuck.

If you think you get a grub menu, but just can't see it, press the down arrow repeatedly and enter.. The windows boot option should be at or near the bottom of the menu

PS if you get it working and want to reinstall, you can retrieve data from the wubi install (from the root.disk). Do this before uninstalling or it will be erased.

---

