---
title: "gnome panel"
date: 2010-11-28
forum: General Help
---

### Post by xdweaver on 2010-11-28
I updated ubuntu to 10.04 and I cant seem to get the panel on the top of the screen to work. In ter i do sudo gnome-panel reset and it works but the goes away any ideas

---

### Post by wojox on 2010-11-28
Try these two commands in the terminal:

```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

You may have to log out and back in.

---

### Post by WorMzy on 2010-11-28
In the (rather unlikely) event that wojox's commands don't work, can you be more specific? What doesn't work exactly? Does the panel not appear? Does it appear but remain unresponsive? Does it appear, and is responsive, but doesn't allow you to edit it? Is there a particular applet that doesn't work? What?

---

