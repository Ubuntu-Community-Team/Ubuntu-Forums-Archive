---
title: "The X button moved!"
date: 2010-04-11
forum: General Help
---

### Post by Speedwagon on 2010-04-11
I did the 10.04 upgrade, and now my close, max, min buttons are all on the left side of the windows.  I want them back on the right side.  How do I fix this, please?

---

### Post by Bob Bertrands on 2010-04-11
maybe a stupid question but did you try changing the theme?

---

### Post by sisco311 on 2010-04-11
```
gconftool-2 --type string --set /apps/metacity/general/button_layout ":minimize,maximize,close"
```

---

### Post by Speedwagon on 2010-04-11
> **Bob Bertrands said:**
> maybe a stupid question but did you try changing the theme?

No, I did not.  This happened as soon as it booted into 10.04, on its own.

> **sisco311 said:**
> ```
gconftool-2 --type string --set /apps/metacity/general/button_layout ":minimize,maximize,close"
```

Awesome, that fixed it.  Thanx!

---

