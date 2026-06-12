---
title: "Disable auto-sleep when battery is critically low"
date: 2011-09-21
forum: General Help
---

### Post by Ficik on 2011-09-21
Reason:
My laptop has hw bug in battery indicator. It shows zero all the time. So when I unplug power cabel it does to sleep. It's not really good while I can still work on it for a hour.

Question:
How do I disable this auto-sleep "feature". There is only "power off" and "hibernate" options in power settings dialog. (using 11.10 beta and really like it)


P.S. I hate people who remove these "disable this stupid feature" options just because they like it.

---

### Post by Beacon11 on 2011-09-21
Easy peasy, but obviously be careful to shut it down in time. In terminal, run:

```

gconf-editor
```

Navigate to apps-->gnome-power-manager-->actions and change the value of critical battery to "nothing."

Are you sure it's a bug, or do you need a new battery?

---

