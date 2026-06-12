---
title: "Nvidia: GLX"
date: 2006-05-14
forum: General Help
---

### Post by twiistedkaos on 2006-05-14
This is part of my error log:
```

(EE) Failed to laod /usr/X11R6/lib/modules/extensions/libglx.so

```
Now X loads up and everthing but I am unable to use opengl because this module isn't loading correctly. I looked in the folder and to my surprise the file is there, the only explanation I can come up with is that it's corrupted somehow. Today I tried to install the "most recent" version of the drivers off the Nvidia website but that caused Nvidia to crash so I had to revert back to the "nv" driver in order to get to my desktop, so I removed nvidia-glx, and reinstalled it to get the 7667(I beleive) version off the repositories. Edited my Xorg.conf file to use that driver instead of "nv" and walla, I had my nvidia again, I soon noticed my opengl screensavers / games were no longer working(they did before). Any solution?

---

### Post by Dr. Nick on 2006-05-14
start by posting a copy of you xorg.conf

---

