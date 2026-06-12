---
title: "Can't log in after restart (9.10)"
date: 2009-11-01
forum: General Help
---

### Post by Korose on 2009-11-01
After being unable to shutdown my computer (nothing was happening when I used the button in the top right), I sudo shutdown -h now. When I tried to log in, I accidentally typed in the wrong password the first time. The second time, it began to log in (I got the password right), the screen flashed a couple of times, but then it goes right back to the log in screen.

---

### Post by collinp on 2009-11-01
It sounds like X is crashing after coming from GDM.

Unfortunately, I can't offer much more than that because I can't remember where X logs to, if it does at all.

---

### Post by Korose on 2009-11-01
> **Hellow said:**
> It sounds like X is crashing after coming from GDM.
 
Unfortunately, I can't offer much more than that because I can't remember where X logs to, if it does at all.
 
is it /var/log/Xorg.0.log

---

### Post by Korose on 2009-11-01
I noticed something interesting... my GUI at the login screen is not showing any options for sessions. The "sessions" menu isn't there at all.

---

