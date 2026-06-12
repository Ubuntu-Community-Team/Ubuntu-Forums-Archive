---
title: "Wacom Tablet - Relative Coordinates"
date: 2010-04-27
forum: General Help
---

### Post by gunksta on 2010-04-27
By default, my Wacom tablet uses absolute coordinates. In comparison a  mouse uses relative coordinates. 

I'd like to set up the tablet to work more like a mouse, which I think  will make the tablet easier to use on some of the large photographs I  want to touch up.

Problem - even after reading the community documentation, I don't know  how to do this or if it's even possible.

Any ideas?

---

### Post by Favux on 2010-04-27
Hi gunksta,

It depends on what release of Ubuntu you are in but generally it would look like:
```
xsetwacom set stylus Mode Relative
```
See:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)
> Mode           Relative|Absolute        sets the mode of the device

You could add it to wacomcpl's .xinitrc if needed.

---

### Post by gunksta on 2010-04-27
Thanks! That gives me something different to look for / Google for. Once I read a little more about it, I'm sure I'll be able to make it work.

Does a Wacom tablet default to absolute or relative coordinates on Windows? It seems like using absolute coordinates is just a pain.

---

### Post by Favux on 2010-04-27
Hi gunksta,

They all pretty much default to absolute I think.  The new Bamboo P & T's touch does default to relative I believe.

Again, can't give you too much help without knowing whether you're in Hardy, or Karmic, or whatever.

---

### Post by gunksta on 2010-04-27
Interesting.

I'm running Lucid on all of my systems. I like to beat the rush. . . . . that's just around the corner.

---

### Post by Favux on 2010-04-27
OK, Lucid.  So you only have the linuxwacom kernel driver since the linuxwacom X driver has been replaced with xf86-input-wacom for Xserver 1.7.  So the xsetwacom commands were rebuilt and there isn't a wacomcpl for it yet.

So to see what the Wacom devices are being called enter in a terminal:
```
xinput --list
```
Then use the device name for the xsetwacom command.  It would look like:
```
xsetwacom set "device name" Mode Relative
```

---

