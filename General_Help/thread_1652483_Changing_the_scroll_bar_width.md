---
title: "Changing the scroll bar width"
date: 2010-12-24
forum: General Help
---

### Post by RedRat on 2010-12-24
I have looked and cannot find how to change the width of the scroll bars, I find mine a bit too small, i would like to make them wider. How do you do that in 10.04?

---

### Post by noah++ on 2010-12-25
Edit or create **~/.gtkrc-2.0** with these lines.
```
style "scroll"
{
    GtkScrollbar::slider-width = 25
}

class "*" style "scroll"
```
Adjust that number to your liking.

---

### Post by RedRat on 2010-12-26
> **noah++ said:**
> Edit or create **~/.gtkrc-2.0** with these lines.
```
style "scroll"
{
    GtkScrollbar::slider-width = 25
}

class "*" style "scroll"
```Adjust that number to your liking.
Thanks it worked!! Simple when you know how.

---

