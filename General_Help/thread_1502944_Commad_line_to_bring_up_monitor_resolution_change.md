---
title: "Commad line to bring up monitor resolution change"
date: 2010-06-06
forum: General Help
---

### Post by aplonis on 2010-06-06
I mis-clicked and now my monitor resolution is WAY too high. I could fix that by re-clicking, but the menu to bring up the screen I need to click is off-screen.

By blind clicking I got a command line window. Can anybody tell me the command line to bring up the system preference for monitor resolution? Then I'll re-click appropriately.

Thanks

---

### Post by realzippy on 2010-06-06
```
gnome-display-properties
```

opens it.If you cannot reach your terminal also:   ALT+F2

---

### Post by KeyserSoze93 on 2010-06-06
If it's too high even to see the dialogue properly, you can change it temporarily by pressing CTRL-ALT-F1, logging in, and running:

```

DISPLAY=:0 xrandr -s 1024x768

```

Then press CTRL-ALT-F7, and hopefully, the resolution should have changed.

---

