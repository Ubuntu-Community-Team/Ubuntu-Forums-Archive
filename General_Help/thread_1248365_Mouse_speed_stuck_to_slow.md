---
title: "Mouse speed stuck to slow"
date: 2009-08-24
forum: General Help
---

### Post by anaconda on 2009-08-24
My mousepad was too fast, so I went to:

System>Preferences>Mouse

And tried to adjust "Pointer Speed", But when I touched the slide bar it went to the slowest speed, and now it wont move back to faster. No matter what.

So does anyone know of a way to adjust mouse speed from somewhere else than "Mouse Preferences" eg. by editing a config file? or something.

I am running Ubuntu 8.04, on an acer aspire one netbook... And I have installed all updates.

Annoying bug.

---

### Post by exutable on 2009-08-24
Try to type in the console:

```
xset q
```

to find what you're current acceleration and threshold is

then accordingly type:

```
xset 2/1 4
```

which is my current acceleration and threshold, obviously fill in what you think should be your acceleration and threshold

---

### Post by anaconda on 2009-08-24
Thank you!

I will try this when I get home.

---

