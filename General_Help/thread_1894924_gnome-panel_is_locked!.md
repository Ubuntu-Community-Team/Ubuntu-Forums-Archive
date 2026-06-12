---
title: "gnome-panel is locked!"
date: 2011-12-13
forum: General Help
---

### Post by x C0MMAND0 x on 2011-12-13
have tried many different work arounds, but no matter what I do gnome-panel is locked. I am ogging in with the "cairo-dock with effects and gnome", and compiz is fully configured and working properly.

I can't right click, alt-right click, or left click or anything to make changes. Additionally, it only shows "applications" and "places", and I would like for it to also show system.

Any tips/advice?

---

### Post by cortman on 2011-12-13
Alt + right click.
It's part of Gnome 3.2 fallback.

---

### Post by x C0MMAND0 x on 2011-12-13
Already tried that, and also, I'm not running Gnome 3.X because I'm running compiz, and compiz isn't compatible with Gnome 3.X

---

### Post by stinkeye on 2011-12-13
> **x C0MMAND0 x said:**
> Already tried that, and also, I'm not running Gnome 3.X because I'm running compiz, and compiz isn't compatible with Gnome 3.X
When playing around with different desktop setups in 11.10, I found I could not
 customize gnome-panel while running compiz.

Switch to metacity...alt+F2
```
metacity --replace
```

Customize panel using alt + Right click

Switch back to compiz...ctrl+alt+t to open terminal
```
compiz --replace & disown
```

---

### Post by x C0MMAND0 x on 2011-12-13
This has helped, metacity allows me to edit gnome-panel, but I can't get compiz to run simultaneously.  I looked at found out when I run compiz-decorator it starts "unity-window-decorator".  I need to have that be metacity but can't seem to figure it out...

---

### Post by stinkeye on 2011-12-13
> **x C0MMAND0 x said:**
> This has helped, metacity allows me to edit gnome-panel, but I can't get compiz to run simultaneously.  I looked at found out when I run compiz-decorator it starts "unity-window-decorator".  I need to have that be metacity but can't seem to figure it out...
I'm a bit confused by all that.
You said you were running compiz as the window manager and also running gnome-panel.
The commands I gave just switched from compiz to metacity as the window manager
and back to compiz.

If you have no window decorations in compiz...
alt + F2 and run
```
gtk-window-decorator --replace
```

---

### Post by x C0MMAND0 x on 2011-12-14
Well, it's a workaround but when I ran "metacity --replace" I was able to edit the panel and customize it completely how I wanted it, then I took back over with compiz.

I still can't edit it, but I have it customized how I want.  If I need to make changes I just have to replace with metacity, make changes, then take back over with compiz and boom.

Thank you for the help.

---

### Post by polki@mac.com on 2011-12-15
You could also try using "alt+super+right click" in the panel.

---

### Post by stinkeye on 2011-12-15
> **polki@mac.com said:**
> You could also try using "alt+super+right click" in the panel.
That's better.
Didn't know that.
=D>

---

### Post by x C0MMAND0 x on 2011-12-16
> **polki@mac.com said:**
> You could also try using "alt+super+right click" in the panel.

That's awesome!  Thank you.

---

