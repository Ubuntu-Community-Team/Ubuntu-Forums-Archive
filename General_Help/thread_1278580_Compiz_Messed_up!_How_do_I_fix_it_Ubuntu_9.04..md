---
title: "Compiz Messed up! How do I fix it? Ubuntu 9.04."
date: 2009-09-29
forum: General Help
---

### Post by Norcoracer25 on 2009-09-29
Hey Everyone, I have ubuntu 9.04 on my asus EEE PC and I was playing around with the effects in compiz fusion and when I restart my netbook, I see my background but when I click on anything, it turns black. When the awn manager comes up its all black to! Can someone please help me fix this???!

---

### Post by tom66 on 2009-09-29
Press Alt-F2, you'll probably get a black window, type "metacity --replace" exactly, press enter. You're now in basic graphics mode (e.g. no effects). Disable all unnecessary effects, then press Alt-F2 and type "compiz --replace", press enter.

---

### Post by Norcoracer25 on 2009-09-29
I tried that but I cant read what it says because every box that pops up is all black.

---

### Post by Norcoracer25 on 2009-09-29
can someone please help me! I need this netbook tonight! I really need help!

---

### Post by langi280179 on 2009-09-29
Turn compositing temporarily off by adding 
```

Section "Extensions"
Option "Composite" "Disable"
EndSection 

```
to xorg.conf

This should prevent compiz from starting. Then you can start to fix your configuration settings.

---

