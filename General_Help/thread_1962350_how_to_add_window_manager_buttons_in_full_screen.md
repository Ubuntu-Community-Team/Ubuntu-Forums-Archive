---
title: "how to add window manager buttons in full screen"
date: 2012-04-20
forum: General Help
---

### Post by Metul Burr on 2012-04-20
In ubuntu unity. How can you add widows manager buttons (close, minimise etc.) to when it is full screen? It is quite annoying to have to do 2 operations (drag down to get access to buttons and then check a button) instead of just one operation. However I did change the direction of the buttons to the right doing:
```
gconftool-2 --set /apps/metacity/general/button_layout \
 --type string "menu:minimize,maximize,close"
```

---

### Post by 3rdalbum on 2012-04-20
> **Metul Burr said:**
> In ubuntu unity. How can you add widows manager buttons (close, minimise etc.) to when it is full screen? It is quite annoying to have to do 2 operations (drag down to get access to buttons and then check a button) instead of just one operation. However I did change the direction of the buttons to the right doing:
```
gconftool-2 --set /apps/metacity/general/button_layout \
 --type string "menu:minimize,maximize,close"
```

In a maximised window, the window buttons are in the top-left corner of the screen (on the left side of the top panel). Move your mouse to the top panel and you will see them there.

---

### Post by Metul Burr on 2012-04-21
OMG, im stupid. Yes they are. I thought since i changed them to the right they would be to the right, i wasn't  even thinking about looking to the left. Plus i have learned to ignore text there. Sorry for the stupid question, thanks BTW.

---

