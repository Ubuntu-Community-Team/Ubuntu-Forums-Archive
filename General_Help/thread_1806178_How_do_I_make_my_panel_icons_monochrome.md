---
title: "How do I make my panel icons monochrome?"
date: 2011-07-17
forum: General Help
---

### Post by BcRich on 2011-07-17
Hi
like the title says, my gnome panel icons are all sorts of colours that tend to make things on my otherwise greyscale desktop look a little unsightly. so is there a way of just changing the color of the icons on the gnome panel to monochrome, and not messing up my other theme settings? aside from the obvious answer of creating a monochrome icon for each individual icon on my panel?
I'm using 10.10 ubuntu studio

---

### Post by Matt__ on 2011-07-17
Have you tried gnome colour chooser from the software center?

Not tried it myself, but it seem to have what you need.

---

### Post by BcRich on 2011-07-17
hi [Matt__]("http://ubuntuforums.org/member.php?u=910572")
I had not heard of that so thanks for letting me know about it :)
it does a lot of gnome color changing, but unfortunately changing panel icons to monochrome is not one of them. nifty gadget to have nonetheless.

---

### Post by Matt__ on 2011-07-19
sorry it was no help...how about you make copies of all the icons used, then make them greyscale using gimp or command line imagemagick.
```
convert icon.png -colorspace gray icon.png
```
Im sure you could use wildcards (*) to batch convert them all at once and even convert recursively (-r) through directories (if you can live with a whole world of grey :P )

---

### Post by 23dornot23d on 2011-07-19
The [Elegant Awoken icons]("http://gnome-look.org/content/show.php/Elegant+Gnome+Pack?content=127826") are almost all grey scale .....

_*[Screenshot of my Desktop]("http://img837.imageshack.us/img837/9682/screenshot1ob.jpg")*_ - shows the ones that may need to be altered

---

### Post by stevenswall on 2012-07-08
This is a common problem, especially with the new Unity. Many icons are not monochrome, and skype, wuala, spideroak, easystroke, etc. are not monochrome. Here is the fix that works for any icon.

(See attached image)

Terminal: <sudo apt-get install xdotools>
Startup Applications: Add <sh -c "sleep 5s; xdotool key ctrl+alt+f" &>

Compiz: Enable Color Filtering, match the toggle key to the one used in the startup applications settings.

Arrange color filters to match those in the screenshot.

Filtered windows: <Type=Dock>
Exclude windows: <(type=Desktop ) | type=Normal>


Hope that helps everyone! A nicer version of this tweak should be implemented in Ubuntu 12.10 to help make all icons monochrome, regardless of whether the program/indicator supports it or not.

---

