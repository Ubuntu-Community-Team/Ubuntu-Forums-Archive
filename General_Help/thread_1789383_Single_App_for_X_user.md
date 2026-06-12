---
title: "Single App for X user"
date: 2011-06-23
forum: General Help
---

### Post by jfreak53 on 2011-06-23
Is there a way that I can have a user on my Ubuntu 11 box that when logged in it automatically opens X program and nothing else, no window manager nothing, single program for that user only?

Here is the scenario, I have 3 users, one is called Skype.  I want when someone logs into the skype user no window manager at all be available to that user from the GDM and for xwin to automatically start skype up.  Any ideas?

---

### Post by LordNeo on 2011-06-23
You can add the program using the "System->Startup Applications" and when double checked, just delete the gnome-panel (or unity panel) so the user is unable to reach the programs (at least not in a easy way).

---

