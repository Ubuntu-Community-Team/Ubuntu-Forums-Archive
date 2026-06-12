---
title: "default gnome terminal window size"
date: 2009-09-05
forum: General Help
---

### Post by blur xc on 2009-09-05
When I open a terminal window, often the first thing I do is resize it bigger.  Is there some magical way that I can make it open up larger by default?

thanks,
BM

---

### Post by imhotep59 on 2009-09-05
Modify the properties of the launcher as follow
```
gnome-terminal --geometry 1024x768
```
Of course you can change 1024x768 according to the size of your screen.

---

### Post by misfitpierce on 2009-09-05
It also auto sizes based off the size of the font... you can go to fonts and chance the one thats at monospace by default 2nd from bottom I believe in font window and if you make it bigger the terminal will be bigger by default too... or you can do the geometry thing as said!

---

### Post by nothingspecial on 2009-09-05
I have a resolution of 1440x900

However my fullscreen gnome-terminal keyboard shortcut binding is ```
gnome-terminal --geometry 178x51 -x dvtm
```

I thought the geometry flag in the gnome-terminal command referred to the amount of characters rather than the resolution.

Maybe you have an enormous screen.........


.........or a tiny font.


However, I stand to be corrected :D

---

### Post by imhotep59 on 2009-09-05
Maybe you're wright nothingspecial but the --geometry option works fine for me and the man page for gnom-terminal says:
```
 --geometry=GEOMETRY X geometry specification (see "X" man page), can be specified once per window to be opened.

```
So, it clearly refers to the X geometry, not to the size ofthe font. The man page for X indicates that these parameters correspond to the size of the windows (width x height). :)
[http://www.x.org/archive/X11R6.8.1/doc/X.7.html#sect6]("http://www.x.org/archive/X11R6.8.1/doc/X.7.html#sect6")

---

### Post by blur xc on 2009-09-05
> **imhotep59 said:**
> Maybe you're wright nothingspecial but the --geometry option works fine for me and the man page for gnom-terminal says:
```
 --geometry=GEOMETRY X geometry specification (see "X" man page), can be specified once per window to be opened.

```So, it clearly refers to the X geometry, not to the size ofthe font. The man page for X indicates that these parameters correspond to the size of the windows (width x height). :)
[http://www.x.org/archive/X11R6.8.1/doc/X.7.html#sect6](http://www.x.org/archive/X11R6.8.1/doc/X.7.html#sect6)

At least on my system --geometry 100x45 generates a terminal 100 x 45 characters.  I originally set it to be 800 x 600, and it was pretty darn big.  WAY off the screen.

Anyway, thanks for the help.  I was looking all through gconf-editor and couldn't find anything.  :confused:

BM

edit- one oddity.  Using my keyboard shortcut it comes out the right size, but the same parameters in my awn dock launcher net a terminal window 100x46.  So, I set that to 100x44, and it comes out 100x45.

---

### Post by kerry_s on 2009-09-05
if you want you can try roxterm, it's faster & you can set the size in the settings.

---

### Post by nothingspecial on 2009-09-05
Wasn`t trying to be clever there. I wasn`t sure.

I learn`t about the geometry flag back in the day when I wanted a big blingy fullscreen transparent terminal.

Nowadays I find it more useful for it to open at it`s default size and press Alt+F10 to full screen it, then Alt-F5 if I want it small again.

---

