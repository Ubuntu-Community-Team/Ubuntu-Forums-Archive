---
title: "black screen after autologin"
date: 2010-06-16
forum: General Help
---

### Post by zx5000 on 2010-06-16
I have noticed that with auto login enabled the power management black screen comes on if I do not issue any mouse or keyboard events withing an hour (or less). All power management settings are set to never and screen saver is not enabled.

For my personal desktop (HP tc4400) this isn't much of an issue but I created an appliance (Zotac MAG) for my company that boots into a specific user with a task monitor in the start-up applications. These units are deployed without mouse and keyboard so after 30 minutes the screen goes black.

A workaround is to fake mouse events with uinput events but I'd like to know if there is a configuration setting that I have missed along the way.

TIA

Jeff

---

### Post by philinux on 2010-06-16
How about system>prefs>startup apps.

Untick power manager.

---

### Post by zx5000 on 2010-06-16
Thanks for your quick response. 

I tested un-checking the power manager but it actually made the problem worse. Now instead of only blanking the screen once it blanks it every 15 minutes. I do not have a xorg.conf file on the test system and I don't know what X defaults to on DPMS settings.

Thanks again.

Jeff

---

