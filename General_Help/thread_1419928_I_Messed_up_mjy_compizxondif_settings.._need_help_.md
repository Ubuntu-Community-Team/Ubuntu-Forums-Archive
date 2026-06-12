---
title: "I Messed up mjy compizxondif settings.. need help please"
date: 2010-03-02
forum: General Help
---

### Post by leeman101 on 2010-03-02
I was messing with some settings in compizconfig settings manager, and i made the window for the manager absolutely transparent..  now i cannot see it.  Stupid of me, i know.  So because i cannot see the window i canot change the settings back from that window..  how can i fix this?  lol.  Lesson learned....

---

### Post by pastalavista on 2010-03-02
You can reset Compiz back to defaults by deleting the ".compiz" folder in your home directory. Make sure Compiz isn't running before you do this (set "Visual Effects" in System|Preferences|Appearance to "none")

```
rm -rf .compiz
```

Then reactivate effects and Compiz will be back to the default settings.

---

