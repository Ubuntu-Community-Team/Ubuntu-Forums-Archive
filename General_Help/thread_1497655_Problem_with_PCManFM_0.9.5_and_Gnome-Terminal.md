---
title: "Problem with PCManFM 0.9.5 and Gnome-Terminal"
date: 2010-05-30
forum: General Help
---

### Post by VastOne on 2010-05-30
Using the new PCManFM 0.9.5 which comes bundled with "lxterminal %s" as the terminal to use in preferences.

Changing it to xTerm %s works fine but changing it to gnome-terminal %s does nothing.  No error, no messages, nothing at all.

Anyone else seeing this?

---

### Post by drs305 on 2010-05-30
After reading your post I opened pcmanfm and changed the setting in *Edit, Preferences, Advanced* to:
> /usr/bin/gnome-terminal %s
and now it works fine. Before that, it did as you reported.

---

### Post by VastOne on 2010-05-30
> **drs305 said:**
> After reading your post I opened pcmanfm and changed the setting in *Edit, Preferences, Advanced* to:

and now it works fine. Before that, it did as you reported.

Thank you...I figured it would be something as simple as this.

Marked as solved

---

