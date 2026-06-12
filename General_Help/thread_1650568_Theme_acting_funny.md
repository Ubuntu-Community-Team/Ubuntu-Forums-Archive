---
title: "Theme acting funny?"
date: 2010-12-21
forum: General Help
---

### Post by Viridia on 2010-12-21
Hi there,

I'm using Ubuntu 10.10 (love it, so much better than Windows 7) but the themes can be funny some time. For instance, when I turn the computer on, the top bar, nautilus, and firefox all have oldish looking themes. I can often fix it just by going to appearance and selecting my theme. The file browser, however, stays in that old theme ([http://img51.imageshack.us/i/screenshothm.png/](http://img51.imageshack.us/i/screenshothm.png/)) Any advice on how to fix that/how to prevent it from being like that in the beginning? Thanks.

Regards,
Nick

---

### Post by stinkeye on 2010-12-22
It's caused by gnome-settings-daemon not loading at boot or crashing.

This works for me and happens so regularly that I use a script to fix it.

FixTheme.sh```
#!/bin/bash

gnome-settings-daemon &&
pkill nautilus
```

---

### Post by Viridia on 2010-12-22
Thanks!

---

### Post by bdoe on 2010-12-22
Thanks for that! I had just installed the latest round of updates, including a kernel update, for 10.10, and when I rebooted, all of my icons were screwed up. Your little script fixed it!

---

