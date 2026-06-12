---
title: "problem with &quot;screensaver preferences&quot;"
date: 2011-03-19
forum: General Help
---

### Post by whvw on 2011-03-19
Every time I go to the "screensaver preferences" (System-Preferences (9.10)), the entire system crashes. Nothing to do but hit the reset button. Does anyone have any ideas about this? Other functions in System-Preferences work just fine. Thanks.

---

### Post by stinkeye on 2011-03-19
Try to unset the screensaver back to blank screen and then see if it opens.
```
gconftool-2 --unset /apps/gnome-screensaver/themes
```

---

