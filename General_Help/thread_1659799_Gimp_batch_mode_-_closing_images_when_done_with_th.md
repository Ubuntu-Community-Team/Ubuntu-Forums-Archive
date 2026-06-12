---
title: "Gimp batch mode - closing images when done with them"
date: 2011-01-04
forum: General Help
---

### Post by J V on 2011-01-04
I need to close images I work with when I'm done with them. As an example scenario, I can open several images and work on them, but every time I open them they create new instances in gimp, meaning the gimp could in the end be using several gigs of ram for images I can't even see are there.

Also, I can't start gimp for batch only (Using 2.7 dev version)

```
$ gimp -i -b "(script-fu-thing 1)"
This is a development version of GIMP.  Debug messages may appear here.

(gimp:11407): Gimp-Core-CRITICAL **: gimp_viewable_get_stock_id: assertion `GIMP_IS_VIEWABLE (viewable)' failed
gimp: fatal error: Segmentation fault
```

---

### Post by J V on 2011-01-05
Bump, how to close images?

Edit: Googling with a fresh eye found something:```
(gimp-image-delete IMAGE)
```

---

