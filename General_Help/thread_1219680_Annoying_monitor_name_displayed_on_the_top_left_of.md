---
title: "Annoying monitor name displayed on the top left of the screen"
date: 2009-07-22
forum: General Help
---

### Post by kinderchocolate on 2009-07-22
As the topic suggested, the name of my laptop's monitor (Laptop 15) is displayed on the top left of the screen. It's in light blue, and I don't know how to get rid of it. Does anybody have any idea?

---

### Post by prshah on 2009-07-22
> **kinderchocolate said:**
> As the topic suggested, the name of my laptop's monitor (Laptop 15) is displayed on the top left of the screen. It's in light blue, and I don't know how to get rid of it. Does anybody have any idea?

It should normally only be displayed with System-Preferences-Display is active. Open it, and uncheck (untick) the "Show displays in Panel" option; then apply and close, and see if it goes away.

If that fails, try killing the display-properties (maybe a zombie, leftover process)```
sudo kill gnome-display-properties
```

---

