---
title: "keyboard disabled in 11.04 login screen"
date: 2011-09-16
forum: General Help
---

### Post by mifi on 2011-09-16
My keyboard works ok in BIOS and in Grub.

When the 11.04 login screen appears, the mouse works but the keyboard does not. I cannot type my password.

So I booted into recovery mode and removed my password. After rebooting I was able to log in and after that in Unity, my keyboard was working fine.

I did run apt-get update and apt-get upgrade, but no packages had to be updated.

So it seems the keyboard is disabled only during the login screen. As a workaround, I have set up automatic login, but I would like to fix this.

Does anyone have an idea?

m

---

### Post by raja.genupula on 2011-09-16
give a try 

[http://ubuntuforums.org/showthread.php?t=791975](http://ubuntuforums.org/showthread.php?t=791975)


replace kdm with gdm 
all the best

---

### Post by ajgreeny on 2011-09-16
This is unlikely to be the problem, but is worth checking, so go to your BIOS and make sure legacy usb setting is enabled, if it's available.  You can get to that from a keypress at boot time, but what to press depends on the motherboard, so look carefully after pressing the power button for a quick screen message, eg, "Press Del for setup".

I have a similar problem on my hardware, which multiboots several Linux distros, where I can not choose from the grub menu as the keyboard does not work in the menu unless legacy usb is enabled in the BIOS.  However, I would not expect this to exhibit itself at the login screen, but it's worth checking.

---

### Post by mifi on 2011-09-16
I will try the suggestions above, but I would like to add that all worked fine before today. It's bahaviour suddenly changed...

Could it be related to one of the recent updates?

Weird, is it not?

m

---

### Post by raja.genupula on 2011-09-16
yeah may be its because of recent updates ,try to register a bug about this in launchpad .

---

### Post by TonyPursell on 2011-10-09
Make sure the option "Slow Keys" is not enabled in the Accessibility options - usually an icon with a man in a ring on the right side of the bottom panel at the login screen.

---

