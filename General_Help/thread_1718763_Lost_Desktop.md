---
title: "Lost Desktop"
date: 2011-03-31
forum: General Help
---

### Post by Tourdog on 2011-03-31
My familiar desktop from 10.04 has vaporized.

However, "Applications" Places" System" is down on the bottom strip/panel.   I can operate from there but..... like to get back to the 10.04 screen.   

Also my HPLIP is unavailable I think because of "Lost System Tray"  

What is the easiest way to diagnose and fix this (up to now) perfect Operating System?  Actually the O.S. is perfect .....  just no friendly desktop.

"sudo apt-get install ubuntu-desktop" ???   

Or,  am I simply missing the obvious............   menu item somewhere?

Thank you in advance!

---

### Post by strafe_sawdoffe on 2011-03-31
It sounds like Gnome is starting, but your normal panel and icon sets are missing; is that correct?

If so, maybe give the steps in this article a try: [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

One deviation I'd suggest from those steps: instead of deleting the directories outright, I'd move/rename them and let the OS recreate them; that way you can restore to where you are now if need be.

---

### Post by Krytarik on 2011-03-31
If the bottom line of this is, that your panels are messed up/missing, you can use this command to just restore them to their defaults:
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```If you can't access a terminal because of that, press Ctrl+Alt+T to get one.

Greetings.

---

### Post by Tourdog on 2011-03-31
Strafe & Kyrtaric,

Thanks both for the quick replys:    


Zero file(s) in Desktop folder.   I am working on it.    Before I wrote the first post I had regenerated the Applications, Places & System.   So somehow previously I deleted the default settings of the gui  Gnome........... evidently because there are zero files in my Desktop.

Do I have this right?

TIA again!

---

### Post by Krytarik on 2011-03-31
Sorry, I don't get what's really the current state at your system.

Did you restore the panels now, are they fine?

You say, you have no files in your desktop folder, are you referring to your actual desktop, or to the directory "~/Desktop"?
Are there used to be files?

---

