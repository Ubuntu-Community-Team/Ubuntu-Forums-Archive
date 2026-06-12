---
title: "Synaptic Package Manager"
date: 2010-11-11
forum: General Help
---

### Post by petersull on 2010-11-11
I have installed an item from Synaptic Package Manager, but cannot find it anywhere.

I have searched the whole computer but it doesn't seem to be there.

How do I find and get to use this item?

---

### Post by Rubi1200 on 2010-11-11
Which package did you install?

Some packages are command line only.

Use the locate command in the terminal to find the files or the built-in tools in Synaptic.

---

### Post by petersull on 2010-11-11
I installed abakus.

---

### Post by petersull on 2010-11-11
I tried

locate 'abakus'

in terminal, but it returned nothing. Maybe it goes under a different filename.

---

### Post by mc4man on 2010-11-11
running abakus in a terminal should start.
As far as a menu item should show up in Applications - Accessories
If it doesn't try a restart. If it still doesn't run this in terminal ( this is from 10.10 ubuntu for path to abakus.desktop  -  check in synaptic, highlight abakus -> properties -> installed files to see if path is the same for you (blue highlighted

 ```
cp [COLOR="Blue"]/usr/share/applnk/Utilities/abakus.desktop[/COLOR] ~/.local/share/applications/
```

---

### Post by petersull on 2010-11-11
Thanks very much,

All sorted now after running that command.

It now appears under applications > accessories.

---

