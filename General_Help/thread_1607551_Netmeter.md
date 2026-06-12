---
title: "Netmeter"
date: 2010-10-27
forum: General Help
---

### Post by Tawrtoise on 2010-10-27
What is a good NetMeter equivalent for ubuntu? Gnome, specifically.

---

### Post by Foxheadz on 2010-10-27
You could use some form of conky wich lets you show a bunch of stuff on your desktop (weather, bandwith, date...) just google conky/conky setups and find one you like. I would suggest conky along with conky colors [http://gnome-look.org/content/show.php/CONKY-colors?content=92328](http://gnome-look.org/content/show.php/CONKY-colors?content=92328)

---

### Post by Tawrtoise on 2010-10-28
Okay, this looks exactly like what I'm looking for. I've got conky and conky colors, and I'm trying to configure it (with ./conky-colors (options)). I failed at configuring it once, and I think that was because I got some syntax (or something) wrong in the command, but after that I configured it right however, now I want to go back and change it. I think I'm just making more conkyrc files and it's loading the same one (and therefore, not changing). Any advice on this?

---

### Post by D1rt on 2010-10-28
Have you taken a look at the gdesklets package?  It has some conky-like widgets.  But dont let the ease of this package dissuade you from playing with conky.

---

### Post by Tawrtoise on 2010-10-28
Well, I'm only trying to configure conky colors, which is way easier than editing the conkyrc directly....but, I'm not even sure if I can do that. Or what I can do with it. I just know it was extremely easy to configure it the first time, but now I want to change some looks about it, and can't seem to get it to actually change. 

Btw, after I'm using the command, ./conky-colors (options) I'm killing conky and then restarting it with alt+f2

---

### Post by Tawrtoise on 2010-10-28
I would really love to have this done tonight. I'm really hoping to get [this](http://gnome-look.org/content/preview.php?preview=2&id=92328&file1=92328-1.png&file2=92328-2.jpg&file3=92328-3.jpg&name=CONKY-colors) theme in particular.

---

### Post by Tawrtoise on 2010-10-29
Okay, I figured out what I was doing wrong to edit it. Turns out you need to make install after you edit the rc. But now I'm a little confused on the themes, where it all looks the same :|

---

### Post by Foxheadz on 2010-10-30
Depending on what your wallpaper is different themes are better. For a dark one I would suggest using radiance and for a light one use ambiance. You can always just make a custome one two.

---

### Post by nah40 on 2010-10-30
Network Traffic Manager (NTM) from Sourceforge.

---

### Post by kuric on 2011-10-30
Network Traffic Monitor is great but it was giving me problems in Ubuntu 11.10 Oneiric Ocelot.

It wasn't launching and I got this error in the terminal:

Traceback (most recent call last):
  File "ntm.py", line 67, in <module>
    help= _("print the version number")
NameError: name '_' is not defined

**To solve this:**

$ sudo gedit /usr/share/ntm/ntm.py

Search for:
help= _("print the version number")

Change it to:
help=("print the version number")

---

