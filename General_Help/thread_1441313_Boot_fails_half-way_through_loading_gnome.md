---
title: "Boot fails half-way through loading gnome"
date: 2010-03-28
forum: General Help
---

### Post by bigred1 on 2010-03-28
Karmic was working fine, but now,the Gnome XServer starts fine but thn drops to a CLI only, in the upper-left of the screen. I can run a GUI app from there, but the desktop as a whole is dead.

Starting in recovery mode, I see this message at the menu "Could not access PID file for nmbd." That problem is a known bug with Samba's initialization, but I really don't know if it is related to my problem.

I tried with* apt-get update* and* apt-get upgrade*, but  that did not resolve the problem.

I reviewed recent log files under */var/log*, but saw nothing obvious. Suggestions?

---

