---
title: "Ubuntu freezes"
date: 2010-10-18
forum: General Help
---

### Post by 1Michael1 on 2010-10-18
I recently followed this tutorial to enable RGBA Transparency on my laptop,

[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

And after rebooting, I got the theme working and all but it was just plain horrible so I decided to remove it, went into themes and whenever I click something there, the laptop just freezes and what seems to be my only option is to press the off button and the boot up again. And when I open some window, application it just freezes on me again. The application that seems to work though is Google Chrome, all other I've tried freezes.

To add, I'm running Ubuntu (Accidentaly choosed Lubuntu in the thread name) 10.10.

Thanks,
Michael.

---

### Post by 1Michael1 on 2010-10-18
Bump,

I'm sitting in school and it's quite important since we're doing programming right now and I need the laptop to work.

---

### Post by AndyCee on 2010-10-18
You might be able to change the setting through "Failsafe Gnome". Log out and select it from the "Sessions" menu before entering your password. You should be able to change the setting from there.

Something simple to try anyway.

---

### Post by 1Michael1 on 2010-10-18
Yeah I did that, and when I want to change a wallpaper as an example, it just starts the the Apperance Preferences countless times. It starts it all until I shut down the windows.

---

### Post by 1Michael1 on 2010-10-18
The wallpaper is just all white, can't change it.
If I try to change it, multiply appearance preferences opens (Wallpaper changes to this black weird thing) and I end up having to reboot the computer.

This is how it looks like, 
[[IMG]http://img814.imageshack.us/img814/7906/screenshotbu.png[/IMG]](http://img814.imageshack.us/i/screenshotbu.png/)

---

### Post by 1Michael1 on 2010-10-18
Bump, 

Is there some System Restore in Ubuntu as on Windows?
Because the pc is acting very strange.

---

### Post by 1Michael1 on 2010-10-18
Bump.

---

### Post by AndyCee on 2010-10-19
> **1Michael1 said:**
> Bump, 

Is there some System Restore in Ubuntu as on Windows?
Because the pc is acting very strange.

If you press shift during boot (immediately after the bios has loaded) you should see the GRUB2 menu, which has some recovery options. Have a look through there for something that may help.

By default there is no equivalent to "System Restore". There may be an older kernel available in the GRUB menu, but I don't think that will solve your problem.

---

