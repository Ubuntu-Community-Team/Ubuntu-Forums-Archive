---
title: "Desktop Drapes won't start automatically on login"
date: 2010-01-21
forum: General Help
---

### Post by humphreybc on 2010-01-21
I have it configured in the application settings to do that, and I've checked the Startup Applications and indeed it is listed there.

However when I start up the icon doesn't appear in the tray and my wallpaper won't change every 10 minutes like it's supposed to until I actually go to System > Preferences and run Desktop Drapes manually.

Ideas?

---

### Post by Carbs70 on 2010-01-29
Exactly the same problem here

**Ed** : Found a solution here [URL="https://bugs.launchpad.net/drapes/+bug/292051"]https://bugs.launchpad.net/drapes/+bug/292051
[/URL]

---

### Post by malspa on 2010-09-22
Ran into this same problem using Drapes in Debian Squeeze.  The first solution mentioned at the web page Carbs70 linked to worked for me:

Edit ~/.config/autostart/drapes.desktop to add the following line:

Type=Application

Thanks, Carbs70!

---

