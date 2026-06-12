---
title: "Sharp windows-like font rendering not working"
date: 2010-05-20
forum: General Help
---

### Post by amcsi on 2010-05-20
I am running ubuntu 10.04 and am using nvidia drivers and my resolution is 1680x1050.

I've been trying to get the windows-like font rendering to work, but I'm having problems with almost every font except Tahoma for some reason. I installed microsoft fonts using [this tutorial](http://www.howtoforge.com/sharp_fonts_gnome_p2).

[(LINK) This is how bad the fonts look in google chrome](http://amcsi.jgypk.hu/x/google.png)
[(LINK)This is what my xorg.conf looks like](http://amcsi.jgypk.hu/x/xorg.conf.png)
[(LINK)This is my .fonts.conf, I have anti-alising disabled for all fonts there (I think), so the fonts would be sharp](http://amcsi.jgypk.hu/x/fonts.png)
[(LINK)This is my appearance settings in ubuntu. Theoretically it should be good, according to the same tutorial for installing msfonts.](http://amcsi.jgypk.hu/x/appearance.png)
[(LINK)This shows how my dimensions and resolution should be correct.](amcsi.jgypk.hu/x/resolution_and_dimensions.png) According to the tutorial, the millimeter values should be, depending on the number of pixels:
displaysize = (<pixelsize>/96)*25.4
which matches

oh and please ignore the attachments

how do I fix it so all my fonts look nice and sharp? Please help

---

### Post by dino99 on 2010-05-20
goto system pref appearence

---

### Post by amcsi on 2010-05-28
if only it were that easy...

---

### Post by inso_741 on 2010-05-28
have you tried playing with sub-pixel smoothing and hinting?

---

