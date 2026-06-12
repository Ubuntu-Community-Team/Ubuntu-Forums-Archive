---
title: "How do I resume without a password?"
date: 2011-05-15
forum: General Help
---

### Post by belltown on 2011-05-15
I'm using Ubuntu 11.04. I've configured my system for Automatic Login so that when I re-boot I do not need to enter a password. This feature works correctly. However, when I resume from a suspended state it asks me for a password to unlock myself. Is there any way of setting it up so I do not have to enter a password when resuming from sleep?

---

### Post by cherva on 2011-05-15
Try to: 
Go System > Preferences > Screensaver and uncheck the box that says lock when screensaver is active.

If this don't work for you try this instead:
1. Start "gconf-editor" from Terminal.
2. Find the  "/apps/gnome-power-manager/lock/use_screensaver_settings" option.
3. Switch off "lock_on_suspend" (and some of the other lock parameters too if needed)

---

### Post by belltown on 2011-05-15
> **cherva said:**
> Try to: 
Go System > Preferences > Screensaver and uncheck the box that says lock when screensaver is active.

If this don't work for you try this instead:
1. Start "gconf-editor" from Terminal.
2. Find the  "/apps/gnome-power-manager/lock/use_screensaver_settings" option.
3. Switch off "lock_on_suspend" (and some of the other lock parameters too if needed)

Thanks, that worked! Unchecking the box on the Screensaver preferences only turned off the password when the screensaver was active. However, unchecking all the boxes with gconf-editor under /apps/gnome-power-manager/lock turned off the password when resuming from suspend/hibernate, etc.

---

### Post by kevinvinv on 2011-06-26
Hi All,  I've tried the items mentioned and still get prompted for a password upon resume from suspend...   any other ideas?  I sure would like to shut off the password dialog...

---

### Post by mcduck on 2011-06-26
> **kevinvinv said:**
> Hi All,  I've tried the items mentioned and still get prompted for a password upon resume from suspend...   any other ideas?  I sure would like to shut off the password dialog...

Are you using the shutdown menu (in the top right screen corner) to suspend? If you do that, no setting will prevent the session from getting locked and asking for a password when you resume.

Suspend through any other menu, widget, or keyboard shortcut, and the settings from cherva's posts should work.

---

### Post by kevinvinv on 2011-06-26
I was using that menu - yes... but alas,  still even using other means- I get the password box... I guess I can live with it...

---

### Post by paulehoffman on 2011-07-05
FWIW, I had the same problem. Don't even bother with the "System > Preferences > Screensaver" bit: it doen't affect suspend. The gconf-editor fixes it fine.

---

### Post by soryu on 2011-11-01
gconf-editor worked.:KS

---

