---
title: "New Theme (10.04)"
date: 2010-05-07
forum: General Help
---

### Post by Kelvrin on 2010-05-07
I love the new defult theme however the close, maximize and minimize buttons are on the left of the screen instead of the right. Is there a way to move thoes back to the right side of the screen?

---

### Post by WinterRain on 2010-05-07
```
gconftool-2 --set “/apps/metacity/general/button_layout” --type string “:minimize,maximize,close”
```

---

### Post by Hangwire on 2010-05-07
Of course!
Run 
```
gconf-editor
```

Then find the following key 

apps \ metacity \ general

There, find an option that says button_layout, double click it and edit it to

```
menu:minimize,maximize,close
```

---

### Post by Ginsu543 on 2010-05-07
Or, if you want a GUI to do the same, download and install Ubuntu Tweak. Under Desktop --> Window Manager Settings, you can change the position of the buttons and the title bar by simple drag-n-drop.

---

### Post by Kelvrin on 2010-05-07
Thanks guys. I appreciate it. :popcorn:

---

