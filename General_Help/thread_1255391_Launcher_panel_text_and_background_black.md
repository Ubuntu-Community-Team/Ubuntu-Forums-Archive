---
title: "Launcher panel text and background black"
date: 2009-09-01
forum: General Help
---

### Post by nabbster on 2009-09-01
Hi guys,

Firstly i am new to linux in general so go easy on me. I am running ubuntu 9.04 x64 I have a problem with some thing called launcher possibly caused by my selection of theme but basically the lanucher panel where you set up a new launcher/shortcut well its back ground is black along with its text making it hard to read.

Is there an option/setting i can use to change this manually?

Thanks

---

### Post by P4man on 2009-09-01
use another theme? 
System > preferences > appearance.

If thats not it, please post a screenshot, as Im not sure I understand the question :)

---

### Post by nabbster on 2009-09-01
Hi this is what i am refering to

---

### Post by P4man on 2009-09-01
thats a problem with the theme. Its putting the background intended for the panel ("start bar") in that dialogue. If it only appears there, perhaps you can live with it, if it appears elsewhere too, use another theme. What theme are you using?

Perhaps see if you like any of these:
[http://www.bisigi-project.org/?page_id=6&lang=en](http://www.bisigi-project.org/?page_id=6&lang=en)

---

### Post by nabbster on 2009-09-01
So no way of over riding this in a setting sone where? its a vista type theme, i know i know windows sux hence i am here but i did like the vista look so i got some thing similar

---

### Post by CatKiller on 2009-09-01
> **nabbster said:**
> So no way of over riding this in a setting sone where?

Of course. It's specified in a setting somewhere, which means it can be corrected somewhere.

Editing GTK themes is probably not for the faint-of-heart, though; it can get a bit complicated, as you can see by the fact the author of that theme got it wrong.

Your options as I see them are

Find a new dark theme that you like. There are thousands. And other people seem to have a Vista fetish too, so you should be able to find something else that you like. This is nice and easy.

Install *gnome-color-chooser*. This is a point-and-click way to change the colour of graphical interface elements. That might let you change the dialogue to something less broken. Quite easy. Might not work.

Find the gtkrc file for the theme you're using and change the appropriate style element to fix that glitch. This will get you exactly the results that you want, but there will be quite a steep learning curve.

---

### Post by P4man on 2009-09-01
there is yet another option: contact the author of that theme and ask if he can fix it (or has already fixed it) :)

---

### Post by steveneddy on 2009-09-01
Edit the theme colors or install Gnome color chooser.

---

