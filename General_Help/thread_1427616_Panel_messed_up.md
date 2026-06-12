---
title: "Panel messed up"
date: 2010-03-11
forum: General Help
---

### Post by jtwhite on 2010-03-11
Something happened to my panel and I tried adding all the stuff back but its not the same.

Items sent to the panel like xChat won't show up anymore!

How can I fix this?

This is what it looks like now:

[IMG]http://i43.tinypic.com/11lr67t.png[/IMG]

---

### Post by sisco311 on 2010-03-11
add a *Notification Area* to the panel.

or you can restore the default panels by running:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```in a terminal.

---

### Post by jtwhite on 2010-03-11
Thank you so much!

That restored everything but the switch user thing. I get this error:
> 
"The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"."

---

### Post by jtwhite on 2010-03-13
-Bump-

---

### Post by Barriehie on 2010-03-13
Try adding the 'user switcher' back to the panel.  Right click and 'Add To Panel'.

---

