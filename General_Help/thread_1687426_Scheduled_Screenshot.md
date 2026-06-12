---
title: "Scheduled Screenshot"
date: 2011-02-13
forum: General Help
---

### Post by Affrikka on 2011-02-13
Hey everyone,

I have my background as a satellite picture of the earth. Right now I have a scheduled task to grab that picture off the internet (the website updates it every three hours) so my background is a 'live' snapshot of the earth.

I want to set up a scheduled task to take a screen shot every three hours, so that I can see, for example, the way the earth changes over the course of a day...a week, etc.

I already have the Scheduled Task Manager from Gnome, but would anyone know what command I could use to do this?

My biggest problem is figuring out how to change the name of the picture it saves it as every time. (e.g. earth1.jpg, earth2.jpg, earth3.jpg, etc.)

---

### Post by jwcalla on 2011-02-13
You could use "date +%s" to return a unique timestamp.  It will be the # of seconds since the epoch.  Then you can append that to your filename to guarantee sequential order.

But instead of grabbing a screenshot from the desktop or background -- which seems iffy since you have to worry about the icons and windows and all the other stuff -- why not just make a copy of the file you download from the internet?

---

### Post by Habitual on 2011-02-14
a software package exists that can do this for you at [http://mein-neues-blog.de/xplanetFX/](http://mein-neues-blog.de/xplanetFX/)

---

