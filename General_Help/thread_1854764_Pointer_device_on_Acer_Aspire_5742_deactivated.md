---
title: "Pointer device on Acer Aspire 5742 deactivated"
date: 2011-10-05
forum: General Help
---

### Post by g_knap on 2011-10-05
Help.

My mouse pad has been deactivated all of a sudden.
If you need some output from the terminal, please let me know what to press on the keyboard.
I have an Acer Aspire 5742 laptop.

---

### Post by g_knap on 2011-10-05
SOLVED!

I tried Fn+F7 after I had logged in, but this did nothing.

Also tried this in terminal:

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

Did nothing for me.

Restarted the machine, touchpad did still not work, but i pressed Fn+F7 before I logged inn...
Tada! It did the trick, works fine.

---

