---
title: "How do I make my Gnome 2.x panel completely opaque?"
date: 2011-06-19
forum: General Help
---

### Post by linuxuser12345 on 2011-06-19
****Fixed title: How do I make... completely translucent?***

I am trying to spiff up my Ubuntu systems a little bit by messing with the panels and such, but it seems that when I am in "Ubuntu Classic" mode, I can not make the entire panels opaque. Only parts of the panels will be translucent, and the rest will still be solid color.

Can somebody help me here? Thanks! :)

---

### Post by Habitual on 2011-06-19
I fired up Gimp and made a new Image at 1440 x 32 (screen width by (my) panel height).
Advanced Options > Fill with > Transparency. hit the OK button.
File > Save As...> and change the drop-down item that says "All Files" to "PNG Image (*.png) and save and name it ~/Documents/transparent.png

Next Right mouse click on the gnome-panel and select Properties > Background > Background image and navigate and select ~/Documents/transparent.png

NOTE: some theme switching may have to be done as some themes override panel transparency.

Logout|in

---

### Post by Enigmapond on 2011-06-19
This link may prove very helpful. I works like a charm!

[http://www.howtogeek.com/howto/43673/how-to-make-the-gnome-panels-in-ubuntu-totally-transparent/](http://www.howtogeek.com/howto/43673/how-to-make-the-gnome-panels-in-ubuntu-totally-transparent/)

Cheers!

---

