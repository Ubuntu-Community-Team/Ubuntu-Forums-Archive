---
title: "Blue screen of death?"
date: 2011-11-18
forum: General Help
---

### Post by engrin on 2011-11-18
A few days ago I updated the recommended updates from Ubuntu and the next day when I switched on my computer, there was a black screen with a white blinking cursor at the top left and the light for the caps lock on the keyboard was also blinking. The harddrive light was not blinking and what I entered in the keyboard did not show on the blank screen. I manually restarted the computer with the power button and the grub screen came up. I was able to boot using the "linux previous versions option" using a linux version that ended with an 8 (I forget the rest of the name). Each time I shut the computer, the same thing would happen, blank screen with cursor, power down with power button, select old version of linux and everything is ok.

I downloaded a startup manager from synaptic and set grub to select the version that was working automatically so that I wouldn't have to do the blank screen business. Well, now when I start up my computer, it goes straight to a BLUE SCREEN that says memory test. The keyboard is unresponsive and there is no way to get out of it. My computer is a brick now :( 

Any suggestions of how to get around this problem? I've downloaded a new Ubuntu version and plan to make a bootable USB key but where to go from there? Thanks all, I hope I dont lose all my data!!

---

### Post by LinuxFan999 on 2011-11-18
Which version of Ubuntu are you using?

Whichever version it is, your install is broken, so you have to back up your data and reinstall Ubuntu.

---

### Post by Mark Phelps on 2011-11-19
You use unetbootin to make a bootable, Ubuntu installation USB stick.

You can try holding down a SHIFT key when you boot.  IF you get a GRUB menu screen, choose the first Recovery Mode option.  When that finally boots, choose the option to Repair Broken Packages.  If that completes successfully, then choose the option for Normal Boot.

IF it all works out well, that will get you back to a working desktop.

If not, come back.

---

