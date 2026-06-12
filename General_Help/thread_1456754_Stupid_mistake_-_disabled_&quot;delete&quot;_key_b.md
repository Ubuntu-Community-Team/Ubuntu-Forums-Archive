---
title: "Stupid mistake - disabled &quot;delete&quot; key by changing keyboard shortcut"
date: 2010-04-17
forum: General Help
---

### Post by e.m.fields on 2010-04-17
Just made a really dumb mistake.
I accidentally changed a keyboard shortcut in GNOME to the "delete" key. I changed the shortcut back, but now my delete key is disabled.

Any clue how to fix this?

---

### Post by Eraemaajaervi on 2010-04-17
try the following:

```

xmodmap -e "keycode 119 = Delete"

```

on my keyboard the keycode for the Delete-Key is 119, it might differ from your keycode.
to get your keycode, simply type
```
xev
```

and press your Delete-Key. in the output it says "keycode ###" somewhere.
exit the program with ctrl+c

---

