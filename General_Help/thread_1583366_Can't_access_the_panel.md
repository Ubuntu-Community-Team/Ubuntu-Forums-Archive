---
title: "Can't access the panel"
date: 2010-09-27
forum: General Help
---

### Post by LeeLgrqst on 2010-09-27
I made the panel small, and set it to auto hide, and put it on the side of the screen.  Now I can not click on it at all.

I've tried several things, first the obvious, like trying to click on it, with both left and right mouse buttons.  Nothing happens.  I searched Google, but the only post I found didn't really apply to me.  

I am not very experienced with Ubuntu, I'm sure it is something easy but I can not figure out how to get it back to normal.

Any help will be greatly appreciated.

I have Ubuntu 10.04 64.

I've included a screen shot, hope it helps.  It is hard to see, but if you look at the middle of the left edge of the image, you will see the shadow of the panel.



> **sisco311 said:**
> Press Alt+F2 and run:
```
gconf-editor
```

On the left pane select apps/panel/toplevels/left(or top/buttom...)_panel_screen0 and try to increase the value of the *auto_hide_size* key or untick the auto_hide checkbox.

This tip worked!   Thank you very much.

---

### Post by sisco311 on 2010-09-27
Press Alt+F2 and run:
```
gconf-editor
```

On the left pane select apps/panel/toplevels/left(or top/buttom...)_panel_screen0 and try to increase the value of the *auto_hide_size* key or untick the auto_hide checkbox.

---

### Post by Dex73 on 2010-09-27
Have you tried alt+f1. It should open Applications thus unhiding the bar. Then right click and change the setting.

---

### Post by raafaell on 2010-09-27
try reopening the panel, alt + f2 and type **gnome-panel --replace** that might help..

---

### Post by LeeLgrqst on 2010-09-27
> **sisco311 said:**
> Press Alt+F2 and run:
```
gconf-editor
```

On the left pane select apps/panel/toplevels/left(or top/buttom...)_panel_screen0 and try to increase the value of the *auto_hide_size* key or untick the auto_hide checkbox.

This tip worked!   Thank you very much.

---

