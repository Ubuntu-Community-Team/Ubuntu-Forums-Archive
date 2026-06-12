---
title: "Alternative For Dia"
date: 2006-06-30
forum: General Help
---

### Post by wizzkid on 2006-06-30
Hi! I tried to use dia to draw my network. However, when I save it as png, its blurry, the text is not readable. 

Can you guys, tell me any alternative software for Dia? :) is there any? 

Thanks a lot.

---

### Post by neutro on 2006-06-30
I'm not sure about any replacement for Dia (altough I think there's a KDE-based Visio clone out there... ah yeah, there it is, "Kivio").

However when saving a Dia drawing to PNG, you are offered a dialog where you can choose the size of the PNG file, in pixels. If you have a rather large drawing and the number of pixels is not high enoug, the PNG will be blurry. Try setting a larger size there. For example, say, if you have a 1024x768 display and your drawing fits nicely in the screen, try setting the height of the PNG to 768. The width will auto-adjust, and the PNG should be identical to your drawing.

Alternatively, you can generate a vector drawing out of your Dia file. You can for example save in .EPS format (choose the one with the PostScript Latin-1 fonts). Dia doesn't offer you to export to .PDF, but once you have the .EPS file, you can do:
```
epstopdf <yourfile.eps>
```
and a file <yourfile.pdf> will be created. This may require that you install epstopdf, but this is a breeze. Vector graphics won't suffer from blurry display since they are infinitely zoomable.

---

### Post by reclusivemonkey on 2006-06-30
If you get stuck and want to try something new there is always Gliffy;

[http://www.gliffy.com/](http://www.gliffy.com/)

I've not used it myself but it could work for you.

---

### Post by barisurum on 2006-06-30
I dont know if its an absolute alternative but inkscape is a perfect vectoral based drawing apt. gnome apt dough.

---

### Post by wizzkid on 2006-07-02
Hi, I find Kivio a good flocharting/ drawing software. however, is there any plugins for the icons/ drawings? I can use dia's but its in black and white. I want something in 3D or a cool drawing graphics. like colors network peripherals etc. 

Thanks a lot. and looking forward of hearing your feedback.

---

### Post by thingy on 2006-07-02
Prob. not what you want...but I came across these when googling for dia alternatives:

[http://www.linuxdevcenter.com/pub/a/linux/2001/02/15/LinuxAdmin.html](http://www.linuxdevcenter.com/pub/a/linux/2001/02/15/LinuxAdmin.html)

---

### Post by Max Luebbe on 2006-07-02
I occasionally use OpenOffice Draw to do some simple flowcharting, not that fancy, but it gets the job done.

---

### Post by wizzkid on 2006-07-03
Thanks guys, :) really appreciate your inputs

---

