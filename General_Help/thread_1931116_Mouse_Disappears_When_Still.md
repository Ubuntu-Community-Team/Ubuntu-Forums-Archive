---
title: "Mouse Disappears When Still"
date: 2012-02-24
forum: General Help
---

### Post by Fajner1 on 2012-02-24
I'm running Ubuntu 11.10. Whenever I don't move the mouse, it disappears after 1-2 seconds of being still. It reappears again if I move it or press a button. This occurs under Gnome-Shell, Gnome-Session-Fallback, and KDE 4, under Compiz, Metacity, and KWin. I have the proprietary nVidia drivers installed.

---

### Post by Fajner1 on 2012-02-25
I think it might be a problem with Synaptics or somesuch...

---

### Post by Fajner1 on 2012-02-25
Also,this doesn't occur when in the Gnome-Shell overview.

---

### Post by Marric on 2012-04-01
Check if the Unclutter Package is installed and remove it.

```
sudo apt-get remove unclutter
```

[http://unclutter.sourceforge.net/](http://unclutter.sourceforge.net/)

---

