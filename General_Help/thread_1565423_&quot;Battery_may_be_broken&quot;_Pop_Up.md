---
title: "&quot;Battery may be broken&quot; Pop Up"
date: 2010-08-31
forum: General Help
---

### Post by bigb_thedestroyer on 2010-08-31
I have a 3 year old laptop with the original battery and its drained pretty bad.  The "Battery may be broken" popup was driving me insane and this is how you disable it, in case you are in the same situation as me.

Open terminal
```
gconf-editor
```

Drill down to...

apps --> gnome-power-manager --> notify

uncheck the low_capacity checkbox.

This should disable the popup for you if your battery has little life left in it.

Now, if any knows how to disable the Avahi popup, let me know.

---

### Post by phpmonkey on 2010-10-16
Wonderful, just what I needed... thanks! :KS

---

### Post by Smartflight on 2010-10-16
Thank you!
Mine's a 3 year old piece too

---

### Post by noisemonkey on 2010-12-02
thank you. that dialog was annoying.

---

