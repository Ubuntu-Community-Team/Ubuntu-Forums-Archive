---
title: "Enable compositing 10.04"
date: 2012-07-20
forum: General Help
---

### Post by Ditchdoc7893 on 2012-07-20
Hello all! I am having a problem with enabling compositing. I tried to run compiz from the terminal and received the following error:


ryan@ryan-desktop:~$ compiz
compiz (core) - Fatal: No composite extension

Launching fallback window manager
Window manager warning: Missing composite extension required for compositing


Why is there no composite extension and how do I fix this? Any help appreciated!

---

### Post by Wirephire on 2012-07-20
You must enable the composite extension in  /etc/X11/xorg.conf
```
Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```


*~wph*

---

### Post by Ditchdoc7893 on 2012-07-22
When I pull up xorg.conf in gedit there is absolutely nothing there. Is this normal? I would imagine some code would typically be there. Any ideas?

---

### Post by Wirephire on 2012-07-22
> **Ditchdoc7893 said:**
> When I pull up xorg.conf in gedit there is absolutely nothing there. Is this normal? I would imagine some code would typically be there. Any ideas?
Yes, this is normal. The X server doesn't need xorg.conf file anymore because it can gather devices with dbus. The configuration files are now in */etc/X11/xorg.conf.d/*
However if you create a file named xorg.conf in */etc/X11*, the configurations of this file will prevail.


*~wph*

---

