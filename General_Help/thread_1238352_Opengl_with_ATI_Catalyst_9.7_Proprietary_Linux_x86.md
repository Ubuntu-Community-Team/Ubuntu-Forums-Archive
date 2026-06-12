---
title: "Opengl with ATI Catalyst 9.7 Proprietary Linux x86 Display Driver"
date: 2009-08-12
forum: General Help
---

### Post by chaosdesigner on 2009-08-12
Okay so i just installed my system new and installed the ATI Catalyst™ 9.7 Proprietary Linux x86 Display Driver. Everything works quite ok but when i start cairo-dock with opengl grafics it has a black backgorund (the dock), which i interpret for meaning that opengl ist not working. I was pretty sure that opengl grafics should work with this driver, or is it wrong? What are my options for getting opengl working?

---

### Post by fabounet on 2009-08-12
ATI drivers are ugly at the moment.
They don't support OpenGL correctly.

---

### Post by chaosdesigner on 2009-08-12
Is that really the case? This confuses me because i read that the ATI Catalyst Driver since 9.1 have OpenGL 3.0 support. One of these pages for example beeing [[COLOR="Blue"]this[/COLOR]](http://news.softpedia.com/news/Latest-ATI-Linux-Video-Driver-Introduces-Full-OpenGL-3-0-Support-103262.shtml) one.

---

### Post by alphacrucis2 on 2009-08-12
> **chaosdesigner said:**
> Is that really the case? This confuses me because i read that the ATI Catalyst Driver since 9.1 have OpenGL 3.0 support. One of these pages for example beeing [[COLOR="Blue"]this[/COLOR]](http://news.softpedia.com/news/Latest-ATI-Linux-Video-Driver-Introduces-Full-OpenGL-3-0-Support-103262.shtml) one.

OpenGL apps like Stellarium and Google Earth work fine for me with the Catalyst driver, especially since 9.5. Prior to that I did have problems.

---

### Post by chaosdesigner on 2009-08-13
Okay this might be a error with cairo-dock, since when i look on the information page of the ati catalyst control center it says i have opengl version 2.1.8787 installed. This is weird.

---

### Post by ssri on 2009-08-13
cairo-dock's homepage explicitly states that their program's opengl will not work with ati's drivers because they are fubar'd.  So, just use cairo-dock -c

[http://www.cairo-dock.org/ww_page.php?p=Recurrents%20problems&lang=en](http://www.cairo-dock.org/ww_page.php?p=Recurrents%20problems&lang=en)

---

### Post by chaosdesigner on 2009-08-13
Now thats just too bad. Well at least i know now that i cant fix it, wont bug me so much anymore.

Thank you!

---

