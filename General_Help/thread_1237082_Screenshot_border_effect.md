---
title: "Screenshot border effect"
date: 2009-08-11
forum: General Help
---

### Post by mike0020 on 2009-08-11
The gnome screenshot tool allows you to choose an option that will automatically add a border effect to your screenshot however this is only possible when taking a screenshot of the current window. 

I was wondering why I'm not able to do this with region screenshots and if it's possible to override the default settings to allow me to do it.

---

### Post by arky on 2009-08-11
Try to enable /apps/gnome-screenshot/include_border with gconf-editor and see if it works.

---

### Post by jerrrys on 2009-08-11
you also may want to look into this

[http://shutter-project.org/about/](http://shutter-project.org/about/)

---

### Post by mike0020 on 2009-08-11
> **arky said:**
> Try to enable /apps/gnome-screenshot/include_border with gconf-editor and see if it works.

It's already enabled.


> **jerrrys said:**
> you also may want to look into this

[http://shutter-project.org/about/](http://shutter-project.org/about/)

If I can't figure out how to make it work with gnome screenshot, then I'll look into that. Thanks.

---

### Post by mike0020 on 2009-08-11
> **jerrrys said:**
> you also may want to look into this

[http://shutter-project.org/about/](http://shutter-project.org/about/)

I looked into it and on the site I didn't see anything about automatic borders, only an embedded drawing tool implying that I'd have to make the border for each picture I take manually, which is not something I want to do.

---

### Post by mike0020 on 2009-08-14
Can anyone else help me?

---

### Post by mike0020 on 2009-08-19
bump

---

### Post by hipodilski on 2012-03-15
Hi Mike,

You will have to use gconf-editor as prior suggested by jerrys. 
Running:
gnome-screenshot --border-effect=shadow will not work for the current created image. Anyways if you change it permanently using gconf-editor so the shadow effect is on. Screenshots will start having a border drop shadow effect.

I've recently wrote an article, on my blog - [http://www.pc-freak.net/blog/how-to-take-area-screenshots-in-gnome-take-quick-area-selection-screenshots-in-g-linux-and-bsd/](http://www.pc-freak.net/blog/how-to-take-area-screenshots-in-gnome-take-quick-area-selection-screenshots-in-g-linux-and-bsd/)
There very in deep, I've went through the problem, you're bumping at :)

Hope it will help you.

Best,
Georgi

---

