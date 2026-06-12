---
title: "python 2.4 dependency"
date: 2009-11-26
forum: General Help
---

### Post by M4rotku on 2009-11-26
Hey guys,

I´m trying to install a program and one of its dependencies is python < version 2.5.  I have 2.6 as default in 9.10 and use 2.6 for several other programs including my own scripts.  Is there any way I can install python 2.4 for use only by this program without it affecting my other programs?

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-11-30
bump

---

### Post by amingv on 2009-11-30
You can do

```
sudo aptitude install python2.4
```

and run your program with

```
python2.4 myprogram.py
```

Or change the shebang(s) to "/usr/bin/python2.4"

I'm curious, though, what program is this?
Is this program not being currently developed/supported?
If it's from a deb package, it may still not work after you install this...

---

### Post by M4rotku on 2009-11-30
I'm trying to install iceme.  it's a menu editor for the icewm windows manager.  I've been trying to get this program working for a while now and I finally found a .deb, but it's from a few years ago.  I don't think it would work via the method you described.  I would need some setting that would tell this program to always use python 2.4.

---

### Post by M4rotku on 2009-12-04
bump

---

### Post by amingv on 2009-12-04
I checked this IceMe program a few days back and found out that it has been abandoned/discontinued since early 2003. ([http://iceme.sourceforge.net/](http://iceme.sourceforge.net/))
I took a look at the code, but it seems to use some libraries that I'm not familiar with, and which by all means look discontinued, too.

I know this is not the most helpful thing to say, but unless that code is given some serious TLC I think trying to run it would be a waste of time: even if you did get it to execute with python2.4, it will still lack the outdated/discontinued libraries which would also be needed; and even if it did run, there's no telling if it will handle correctly any of the config files it is supposed to manage, as it is very old and IceWM may have made changes here and there in that period of time.

I tried and looked for similar substitute projects/forks, but all IceWM menu editors I could find were discontinued between 2003 and 2005. :(

---

### Post by M4rotku on 2009-12-06
Grr, I just want something that will allow my menus to automatically update as they do in Gnome.  It would be nice to get the same categories as Gnome, but I'm not **too** picky about that.

Currently, I install a new program and it does not appear in the menu.

---

