---
title: "Lost wicd tray icon, cannot get it back"
date: 2009-07-11
forum: General Help
---

### Post by cbraxton on 2009-07-11
I'm using 9.04 Netbook Remix on an Asus Eee 1000HA, and have had wicd installed in preference to network manager.

Tonight while editing the top panel, I accidentally (stupidly) managed to remove the wicd tray icon. Now I can't find a way to get it back. Running wicd-client doesn't display it, and uninstalling/reinstalling wicd does not help. (Neither does rebooting, of course.)

When running wicd-client from a terminal, the following is displayed:

   Loading...
   Attempting to connect tray to daemon...
   Success.
   Done.

...but the tray icon does not appear.

Anyone know how to fix this? (I really don't want to go back to network manager!)

---

### Post by cbraxton on 2009-07-11
Closest I can get to it so far is to just add the wicd-client from the internet menu to the panel using "Add to Panel/Application Launcher."

This doesn't really bring the tray icon back, but at least make it convenient to bring up the wicd dialog box for connecting and disconnecting networks. Would still like to get the tray icon back as it displayed a graphical indication of signal strength.

---

### Post by cbraxton on 2009-07-16
D'oh! Turns out what I actually had removed was the "notification area" -- just added it back and all functionality returned.

---

