---
title: "extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2006-04-22
forum: General Help
---

### Post by AndrewCaul on 2006-04-22
I've installed nvidia-settings and nvidia-glx and enabled it. But when I try to run Planet Penguin Racer, it refuses to open and says 
```
Xlib:  extension "GLX" missing on display ":0.0".
```
What is this GLX extension and what should I do about it?
The nVidia splash screen never showed up either.

---

### Post by AndrewCaul on 2006-04-28
I seem to have solved the problem. I followed the steps in [this thread]("http://www.ubuntuforums.org/showthread.php?t=131267") and modified my **xorg.conf** file appropriately.

---

