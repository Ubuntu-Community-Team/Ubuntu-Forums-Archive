---
title: "Password prompt continues after turning it off in System &gt; Prefs &gt; Screensaver"
date: 2010-08-20
forum: General Help
---

### Post by RonB123123 on 2010-08-20
How do I disable the screensaver password prompt when I've already turned it off in System > Preferences > Screensaver? I tried checking and unchecking the box again and I also tried rebooting.

Another strange phenomenon is that after I enter my password, I'm now disconnected from the wireless network. Any thoughts?

I'm using 10.04 lucid lynx.

---

### Post by cmcanulty on 2010-08-20
I had same problem with our library Ubuntu machines. I just made a new user and that stopped it but not a fix that I would like to do, never found an actual fix.This started with 10.04

---

### Post by gmargo on 2010-08-20
It may be the **gnome-power-manager** interfering.  I think I had the same problem and solved it by opening the **gconf-editor**, navigating to **/apps/gnome-power-manager/lock/**.  Now see if the **use_screensaver_settings** checkbox is checked.  If not, then check it.

---

### Post by RonB123123 on 2010-08-20
Perfect, that setting worked for me immediately! Thank you!

---

### Post by cmcanulty on 2010-08-20
Thanks mine wasn't checked either!

---

