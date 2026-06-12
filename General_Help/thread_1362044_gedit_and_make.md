---
title: "gedit and make"
date: 2009-12-22
forum: General Help
---

### Post by Qvintvs on 2009-12-22
Is there a way to have gedit inset actual tab character when I hit the tab key ONLY while editing Makefiles? normally I much prefer 2 spaces, which is what I have gedit set up to do, but make seems to be picky about its tabs.

I suppose getting make to be less picky about its tabs would help too, but I don't know if that's possible.

---

### Post by rCXer on 2009-12-22
I'm not very familiar with gedit but have a look at [this plugin](http://code.google.com/p/gedit-autotab/).

> 
Auto Tab (0.6)  2009-09-27
  * Special case Makefiles so they always use tabs.
  * Fix proper counting of indentation, patch from danielfalk22 (issue #7)


Gedit is somewhat barebones, if you want to do something more advanced consider using a differnt editor, like KATE.

```

sudo apt-get install kate
sudo apt-get install konsole

```

---

### Post by pbrane on 2009-12-22
Set the tab width to 2 and don't replace tabs with spaces. It's the same spacing.

---

