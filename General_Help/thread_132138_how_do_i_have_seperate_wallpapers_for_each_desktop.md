---
title: "how do i have seperate wallpapers for each desktop?"
date: 2006-02-17
forum: General Help
---

### Post by ren wins on 2006-02-17
a different wallpaper for each desktop. i can change all the desktops to one wallpaper, but it would be nice to be able to tell them apart with a quick glance.


on a slightly related note
how do i set up the screen-savers to be random, like in gnome?

---

### Post by FlakJacket on 2006-02-17
There's a drop-down menu that should say "all desktops" now pick each desktop individually and pick a new wallpaper. Screensaver should have an option.

Flak

---

### Post by PartisanEntity on 2007-04-11
> **FlakJacket said:**
> There's a drop-down menu that should say "all desktops"

Anyone know where this drop down menu can be found?

---

### Post by James.Dehart on 2008-04-07
[http://ubuntuforums.org/showthread.php?t=69507&highlight=wallpapoz](http://ubuntuforums.org/showthread.php?t=69507&highlight=wallpapoz)

This will allow you to do what you want. :) I hope this helps.

---

### Post by James.Dehart on 2008-04-07
I found an even better program to use! 

[http://drapes.mindtouchsoftware.com/](http://drapes.mindtouchsoftware.com/) 

To install open up a command window:

```
sudo apt-get install drapes
```

:)

---

### Post by drs305 on 2008-04-07
I like wallpapoz but saw a lot of scripting on the link provided. I don't remember it being that difficult. Here are my notes:

Info and download:	[http://wallpapoz.akbarhome.com/index.html](http://wallpapoz.akbarhome.com/index.html)
It's a .tar.bz2 file so you'll have to unpack and install it. Click on the downloaded file and it should open up the folder. The install instructions are in the README file.

To start, add or edit selections via wallpapoz ; startup command is:  daemon_wallpapoz
You can also edit XML file in ~/.wallpapoz/wallpapoz.xml but not recommended
Include in startup sessions (Syst, Prefs, Sessions, Startup Programs: daemon_wallpapoz )

To add a background once you have installed it, right click on the Desktop and select "Change Desktop Background".

---

