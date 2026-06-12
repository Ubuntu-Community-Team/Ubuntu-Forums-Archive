---
title: "Problems w/ Remote Desktop."
date: 2010-10-23
forum: General Help
---

### Post by becho on 2010-10-23
Does any one else have this issue with Ubuntu's Remote Desktop. I am running 10.10 on all my computers and if I try to connect to another PC while it has "visual effects" enabled the screen will not refresh. If I disable effects on the host PC then remote desktop works fine. All PC's running ATI cards with the restricted driver "fglrx". It works but I would like to enable effects on the host.

---

### Post by becho on 2010-10-23
Nevermind, found the fix.

gconf-editor

/desktop/gnome/remote_access and enable "disable_xdamage"

---

### Post by mhgsys on 2010-10-23
well thnx, 

I actually disabled effects because of this problem and did not find it worthy enough to google for a fix. 

Thnx to you I won't have to.

---

### Post by becho on 2010-10-23
You are welcome, now back to installing AWN on host!

---

