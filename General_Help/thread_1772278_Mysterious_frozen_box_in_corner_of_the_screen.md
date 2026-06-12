---
title: "Mysterious frozen box in corner of the screen"
date: 2011-05-31
forum: General Help
---

### Post by OFC on 2011-05-31
[http://i.imgur.com/Zc8BZ.png](http://i.imgur.com/Zc8BZ.png)

In the upper left corner of my screen, under my the applications menu, there's a small square that remains frozen no matter what I do, when I click on it, it responds as if it's not there, ie my desktop or current maximised window responds instead. Picture it attached.

---

### Post by Toz on 2011-05-31
If you change the desktop background, does the image/remnant remain?

---

### Post by CamD on 2011-12-26
Same issue here with 10.04 LTS.
The xfwm4 display compositor is the culprit.

A temporary fix is to disable and re-enable with the GUI or with the following commands:
```
xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s false
xfconf-query -c xfwm4 -p /general/use_compositing -t bool -s true
```

---

