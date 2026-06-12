---
title: "How do I increase the size of the scroll bars and button"
date: 2011-07-25
forum: General Help
---

### Post by Cammaaron on 2011-07-25
I have a dell inspiron duo, which is a touch-screen tablet hybrid.

And when in tablet mode, it is hard to scroll up and down (its multi-touch ability does not work in ubuntu) and closing and resizing windows.
Any remedy to this?

PS: I use unity, because it is easier to launch applications with a touchsreen in that.

---

### Post by jerrrys on 2011-07-26
got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=resize+scrollbar&as_qdr=all&sa=Google+Search&lang=en#866](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=resize+scrollbar&as_qdr=all&sa=Google+Search&lang=en#866)

---

### Post by Cammaaron on 2011-07-30
That really does not help. period.

---

### Post by Cammaaron on 2011-08-03
bump

---

### Post by jerrrys on 2011-08-03
sorry.  period.

---

### Post by pqwoerituytrueiwoq on 2011-08-03
you can edit the theme's code
if you are using the ambiance theme
```
gksu gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
```
look for GtkScrollbar and slider-width on the same line on line 35 for me but my Ambiance theme has some mods and is not standard
attach a copy and i will edit it tell me how much bigger it needs to be (in pixels or a percentage)

---

