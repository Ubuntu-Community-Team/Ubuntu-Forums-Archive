---
title: "Upgraded to 12.04, and can't make pidgin run in the background anymore"
date: 2012-08-09
forum: General Help
---

### Post by Zorgoth on 2012-08-09
Just what the title says. I want pidgin to keep running when the Buddy List window is closed and ideally to be accessible from the system tray (as it was in 11.04 through the mail icon). However, I cannot get this to happen, even though the "Show System Tray Icon" optino is set to "Always." Is there any way to make pidgin work like this? I don't like Empathy.

---

### Post by Zorgoth on 2012-08-27
Solution (also applies to programs like Skype):

Install dconf-tools.
run dconf-editor (not gconf-editor it seems, it didn't work for me)
desktop > unity > panel contains a whitelist. Just add 'Pidgin' to it. Or 'Skype', or whatever else you want,

---

