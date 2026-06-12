---
title: "Weird keyboard remapping under VNC"
date: 2010-07-28
forum: General Help
---

### Post by StretchyBill on 2010-07-28
I am running a fully updated 9.10 with TightVNC. When I connect in through a TightVNC viewer, my keyboard is mapped wrong. If I type the keys: abcdefg... I get: asdfghjkl;... (the home row)

I tried running this script:
```

#!/bin/bash
echo "" > empty.keymap
xmodmap empty.keymap

```but it didn't help. Any other ideas?

-Bill

---

### Post by StretchyBill on 2010-07-28
One other thing that may be important. I am running a 64bit version.

---

