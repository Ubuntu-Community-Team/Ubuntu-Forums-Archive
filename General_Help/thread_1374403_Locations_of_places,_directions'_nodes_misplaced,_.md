---
title: "Locations of places, directions' nodes misplaced, lumped together"
date: 2010-01-06
forum: General Help
---

### Post by size_XXM on 2010-01-06
After having installed and played with gogleerarth a few times, the location of the rectangular crosshairs is now way off the actual location of the place (according to the map), although the stars/points are placed correctly. It's as if the crosshairs location resolution was drastically smaller and everything was being thrown into a grid with cells ~100 kilometers large. When flying to a location from the search field, the view flies to the right place, but the crosshairs go off the view as it's zooming in. The balloons are pinned to the crosshairs. Zooming out afterwards, it looks like this:
[http://img707.imageshack.us/img707/6785/gefail1.png](http://img707.imageshack.us/img707/6785/gefail1.png)

This also affects directions, which look like this (completely unusable):
[http://img140.imageshack.us/img140/1498/gefail2.png](http://img140.imageshack.us/img140/1498/gefail2.png)

Tidbit: I have my system set up with LC_MESSAGES=en_US and LANG=sk_SK (my location). Apart from GE ignoring the LC_messages variable, I tried running GE with env -u LANG -u LC_MESSAGES, leaving the locale unset (POSIX). The problem seems to have gone away for the time being but the program itself worked fine right after installation, so I expect this "workaround" to die eventually, too.

What's the problem here? No one else encountered this? Happened to me on three separate OS installs already, even without the en_US locale tweak.

Oh yeah - GE installed from medibuntu, of course.

---

### Post by charly8182 on 2010-01-10
I'm having the exact same problem since last month. When I hit a bookmark it goes to the correct location but the bookmark itself is totally misplaced

---

### Post by alphablue52 on 2010-01-23
I have the same problem since a while. I am also a german user, maybe GE wants to mislead us? :confused:

Tried to de- and reinstall all kinds and versions of GE and dep. libs, deleting all config and user files - no way out :(

Kubuntu 9.10, GE 5.1.3509.4636-0medibuntu1 (and others)

---

### Post by alphablue52 on 2010-01-23
This seems to be a problem with the Medibuntu packages. I installed GE as a normal user from the .bin-file of the Google Download page, and no more displacing!
Just one small drawback: the fonts are kinda ugly (no antialiasing).

---

