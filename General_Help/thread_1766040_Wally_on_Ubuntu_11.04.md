---
title: "Wally on Ubuntu 11.04"
date: 2011-05-23
forum: General Help
---

### Post by nekrodamus on 2011-05-23
Hi everyone! I had Wally (2.3.2) working perfectly on my Ubuntu 10.10. When I update Ubuntu to 11.04, Wally dessapear!!
It starts when I turn on the notebook, but it doesn't work (it doesn't change the wallpaper at all) and i can't see it anywhere in the only bar i can see on the top of the desktop (where it used to be).
If i look for it in the terminal, i found it. I can kill it and restart, i see the splash window but nothing else happens.
I upgraded Wally to 2.4.1 and it still the same. I can run it, kill it and run it again, but the walpaper still is the same...
Some help please???

---

### Post by wildmanne39 on 2011-05-23
> **nekrodamus said:**
> Hi everyone! I had Wally (2.3.2) working perfectly on my Ubuntu 10.10. When I update Ubuntu to 11.04, Wally dessapear!!
It starts when I turn on the notebook, but it doesn't work (it doesn't change the wallpaper at all) and i can't see it anywhere in the only bar i can see on the top of the desktop (where it used to be).
If i look for it in the terminal, i found it. I can kill it and restart, i see the splash window but nothing else happens.
I upgraded Wally to 2.4.1 and it still the same. I can run it, kill it and run it again, but the walpaper still is the same...
Some help please???
Hi, a lot of things have changed in natty, somethings that use to work do not now, like conky had to have adjustments made to there scripts a little. Maybe a newer version of that program will come out, or someone can help rewrite the code to make it work.

---

### Post by 3rdalbum on 2011-05-23
Wally uses the old Notification Area system which is depreciated in favour of the new* Indicators system, and so Unity no longer shows notification area icons by default. You can, however, use a "whitelist" to tell Unity to display the notification area icon for Wally, or to display all notification area icons.

The reviews for Wally in the Ubuntu Software Center actually tell you how to do this:

> Get the current whitelist with the following command from terminal:
gsettings get com.canonical.Unity.Panel systray-whitelist

Then set the new whitelist with this command:
gsettings set com.canonical.Unity.Panel systray-whitelist "[ <retype your previous app>, 'wally']"

Logout, login again and launch Wally. You should see app in systray.

(*two years old now!)

---

### Post by bomber1712 on 2011-08-22
I hope that this topic is still monitored...

This worked for me, until the last update (I am running 11.04 and ran the update packages in the last week).  Now, I can start Wally (Alt+F2) and see it's splash screen.  It briefly shows in the sys tray, then disappears.  Never gets started.  Any help is appreciated.

---

### Post by VictorBarrantes on 2011-09-14
> **3rdalbum said:**
> Wally uses the old Notification Area system which is depreciated in favour of the new* Indicators system, and so Unity no longer shows notification area icons by default. You can, however, use a "whitelist" to tell Unity to display the notification area icon for Wally, or to display all notification area icons.

The reviews for Wally in the Ubuntu Software Center actually tell you how to do this:



(*two years old now!)

This command does not work as you suggest, instead you get:

Usage:
  gsettings set SCHEMA[:PATH] KEY VALUE

Set the value of KEY to VALUE

Arguments:
  SCHEMA    The name of the schema
  PATH      The path, for relocatable schemas
  KEY       The key within the schema
  VALUE     The value to set

---

