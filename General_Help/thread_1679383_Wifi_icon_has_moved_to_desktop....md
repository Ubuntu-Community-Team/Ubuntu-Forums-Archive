---
title: "Wifi icon has moved to desktop...?"
date: 2011-01-31
forum: General Help
---

### Post by redsoxrobbe on 2011-01-31
So I've scoured this forum and others and while many have had WiFi icon issues, I've not found a solution to my issue.

The WiFi icon (nm-applet) has moved completely off the panel, and is now all the way to the left side of screen directly under the panel. Thereby making impossible to click to left of icon. No way to unlock it, so I can't move it. 

I've killed and reset the notification area with no luck.
Removed and restored the panel - no luck.
The WiFi indicator stays in same location - far upper left of screen, on desktop, just under the top panel.

Multiple reboots - no luck.

Anyone have any tips on how I can get this thing back on panel?

Of note - I'm on Maverick Meerkat, and do have Cairo Dock.

/thanks

---

### Post by K.abhijit on 2011-02-09
Hey i had a similar issue but on Ubuntu 10.10 with no extra panels. All I did was to delete the directory
~/.gconf/apps/nm-applet and
~/.gconf/apps/panel

Then log out and log back in.
the directories you delete contain configuration settings which are regenerated to default values when you log back in. You may need to locate where the corresponding settings are for your dock.

~Abhijit

---

