---
title: "Completely messed up Ubuntu after upgrade"
date: 2011-10-14
forum: General Help
---

### Post by nimonika on 2011-10-14
I have managed to completely mess up my gnome and unity settings after the upgrade. I have no clue how to revert back to factory settings for both. I changed something for unity via compiz, but it now does not go back to the £D version. Gnome panels are messed up and they do not want to reset as well. Please can someone help.

---

### Post by drs305 on 2011-10-14
For unity, try:
```
unity --reset
```

---

### Post by nimonika on 2011-10-14
I did, it does not work.:(

---

### Post by drs305 on 2011-10-14
Have you tried resetting the defaults via Compiz?
Preferences > Profile: Reset to defaults

Suggestion: If/when you get things back to the way you like, the same Compiz section (Preferences > Profile) has an option to save the profile.

Note: These are from the CompizConfig Settings Manager, which I'm assuming is how you changed the settings in the first place.

---

### Post by egkeat on 2011-10-14
Don't know if this will help but I had to do a restart, then went into Ubuntu 2D via the setting menu. Then I logged out. On the logon screen settings menu, I checked Gnome 3 and went from there. Everything's working again now.

---

