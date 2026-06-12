---
title: "Always on Display (weather, graphs, stocks, rss, slideshow)"
date: 2009-08-03
forum: General Help
---

### Post by mox386 on 2009-08-03
So I have an old dell that I've re-purposed as a display to be always on. I want to display lots of things on it like the local weather radar, a stock list, a picture slide show, etc. I want to have it on 24-7. I had it up doing this before with one one of those windows things for doing such, but it was so damn unstable and wouldn't behave. A month ago it stopped working correctly, so I wiped it clean and began the process of setting it up as a ubuntu box (not a server) specifically for the purpose of displaying information so that I can be seen across the room. 

**My question is twofold does anyone know something that would help me be able to design this "heads up"/"always on" machine?**

Is there a group to join, or anything I'm actually kinda desperate to find out if other people are doing this because I'm sure somebody is. The hope is that this thing behaves and is stable for a LONG time .... a year or two. The aDesklets thing seems inadequate for the job.



list of concepts for display

-Radar map (about 1/4 of the screen)
-Temp/conditions out right now (large)
-24 hour graph of temp
-5 day graph of temp high/low with conditions icons
-Moon Phase
-Pic Slide show that can pull form websites and local folders for it's random photo (probably another 1/4 of the screen)
-Stocks list abot 30
-RSS viewer feed viewer
-Standard system info (yes I get conky can do this)

---

### Post by CatKiller on 2009-08-04
A combination of screenlets and conky will probably get you what you want. They are both sets of scripts that display stuff based on some input. How much you rely on existing scripts and how much you tweak yourself will depend on how comfortable you are with writing scripts.

---

### Post by mox386 on 2009-08-16
Conky looks cool, but there are no screenlets powerful enough for what I want to do. Is there a place where better screenlets are?

---

### Post by CatKiller on 2009-08-16
[http://screenlets.org/index.php/Category:UserScreenlets](http://screenlets.org/index.php/Category:UserScreenlets)

[http://gnome-look.org/index.php?xcontentmode=6700](http://gnome-look.org/index.php?xcontentmode=6700)

Probably a bunch of other places as well.

If you use KDE4, you can use plasmoids to achieve a similar thing. You can use SuperKaramba widgets, Google Gadgets, Web widgets and OS X Dashboard widgets with plasma if there aren't enough options for you already.

How powerful they are depends entirely on how much time you want to put in.

---

### Post by mox386 on 2009-08-16
Well I've been browsing about this for a long time now and I don't think anyone else has re-purposed a machine for use as a display only. I've tried out screenlets but nothing seems to be adequate for the job. I've tried conky but it doesn't work right and doesn't look right from across the room.

What I had going was rainmeter is there anything like that for linux? Is SuperKaramba good? Google stuff doesn't help with what I want

Just to make it clear this is for a machine meant to Display information I am to lazy to look up, the list in the first post should be considered, but also consider that I need to see it from about 20 feet away.

---

### Post by CatKiller on 2009-08-17
> **mox386 said:**
> I need to see it from about 20 feet away.

Unless you have a massive display, this will limit the amount of things that you can show at once.

From your list,

*-Radar map (about 1/4 of the screen)*
Haven't looked for this. Probably easily done as soon as you find a data source.

* -Temp/conditions out right now (large)*
Included by default with screenlets, gnome-panel and plasma.

*-24 hour graph of temp*
Easily done as soon as you find a data source.

*-5 day graph of temp high/low with conditions icons*
Easily done as soon as you find a data source.

*-Moon Phase*
Included by default with screenlets, gnome-panel and plasma.

*-Pic Slide show that can pull form websites and local folders for it's random photo (probably another 1/4 of the screen)*
Included by default with both screenlets and plasma.

* -Stocks list abot 30*
Included by default with screenlets.

* -RSS viewer feed viewer*
Included by default with both screenlets and plasma.

* -Standard system info (yes I get conky can do this)*
Conky will do this, but there are also displays included by default with both screenlets and plasma.

---

### Post by andersja on 2010-03-05
Mox - I'm looking for something similar and found this, which might be helping you forward:

[http://www.burgerfaire.com/index.php/dpflpf/44-laptop-digital-picture-frame](http://www.burgerfaire.com/index.php/dpflpf/44-laptop-digital-picture-frame)
[http://www.burgerfaire.com/index.php/dpflpf/44-laptop-digital-picture-frame?start=1](http://www.burgerfaire.com/index.php/dpflpf/44-laptop-digital-picture-frame?start=1)
[http://www.burgerfaire.com/index.php/dpflpf/45-xml-weather-for-your-dpf](http://www.burgerfaire.com/index.php/dpflpf/45-xml-weather-for-your-dpf)

This will give you CNN weather forecast + news rendered on to images of your choosing - very cool!

Now - it'd be awesome if someone started tinkering with a generic screen saver that could do such "channels" - taking inspiration e.g. from [http://www.framechannel.com/](http://www.framechannel.com/)

---

