---
title: "nautilus error"
date: 2010-01-21
forum: General Help
---

### Post by Cabs21 on 2010-01-21
Having a strange output when using command ```
nautilus
``` in terminal


outputs something like this
```

$ nautilus

(nautilus:2644): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

```

but nautilus opens my home folder with no problems.  any ideas??

---

### Post by Cabs21 on 2010-01-22
bump

---

### Post by warfacegod on 2010-01-22
That looks like it's failing to load your file browser preferences for whatever reason. I get it often when using gksudo nautilus. I don't worry about it because Nautilus starts as root and I can do what I need.

---

