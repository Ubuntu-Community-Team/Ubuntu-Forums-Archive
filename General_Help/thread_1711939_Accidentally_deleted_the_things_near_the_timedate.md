---
title: "Accidentally deleted the things near the time/date"
date: 2011-03-22
forum: General Help
---

### Post by prettymess on 2011-03-22
You know, the section where the wireless signal and sound control is?

To the left of the time/date in this picture:
[IMG]http://img696.imageshack.us/img696/7260/screenshotfk.jpg[/IMG]

How can I get it back?

---

### Post by Script Warlock on 2011-03-22
right click the top panel "add to panel" add indicator applet.

---

### Post by prettymess on 2011-03-22
Thanks for the response, but that didn't exactly work.  But I figured it out anyway.  For anyone else that might have this problem just do this:

```
gconftool --recursive-unset /apps/panel

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

and it'll reset the panels to their default settings.

---

