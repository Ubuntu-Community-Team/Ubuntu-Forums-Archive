---
title: "My GUI is gone"
date: 2011-08-30
forum: General Help
---

### Post by narps on 2011-08-30
Hi,
I'm running Ubuntu 11.04. I recently installed CompizConfig Settings Manager. I was playing around with it a bit, but when I turned on "desktop cube", my screen got all choppy and buggy, so I shutdown the computer. Now when I turn it on and log in, I can see my desktop wallpaper, but that's it. No icons, no bar at the top, no bar on the side, etc. Additionally, when I try to open a terminal with Ctrl-Alt-t, nothing happens. However, I am still able to switch to console mode via Ctrl-Alt-F1. Any ideas on how to fix this? Thanks alot.

---

### Post by ajgreeny on 2011-08-30
Use the command ```
compiz --reset
```which should put things back to the default.

There are many incompatibilities between compiz and unity, so it is best not to enable any compiz plugins that are not enabled by default.

---

### Post by narps on 2011-08-30
fixed. Thanks!

---

### Post by ajgreeny on 2011-09-02
Sorry, that should have been ```
gconftool-2 --recursive-unset /apps/compiz
``` followed by ```
unity --reset
```

---

