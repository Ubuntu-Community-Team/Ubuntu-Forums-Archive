---
title: "Issue with ATI Card"
date: 2011-08-07
forum: General Help
---

### Post by rmausser on 2011-08-07
I have a computer with an ATI card, and whenever I try to load Google Earth or an OpenGL game I get this error:

"extension "GLX" missing on display ":0.0"."

I thought GLX was for Nvidia cards... what is going on?

Someone help please.

---

### Post by LowSky on 2011-08-08
Have you installed the proprietary driver?

Also GLX is a OpenGL extention for X system.

[http://en.wikipedia.org/wiki/GLX](http://en.wikipedia.org/wiki/GLX)

---

### Post by Mark Phelps on 2011-08-08
If you know the make and model of the ATI card, then tell us.

If you don't, then open a terminal and enter "lspci", look for the line containing "VGA" -- and post that info here.

If your card is one of the ATI "legacy" cards, then there is no new driver you can install for it.

---

