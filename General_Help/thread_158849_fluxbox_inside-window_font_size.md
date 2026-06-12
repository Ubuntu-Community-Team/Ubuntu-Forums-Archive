---
title: "fluxbox inside-window font size"
date: 2006-04-11
forum: General Help
---

### Post by antiemptyv on 2006-04-11
How can i change the font size of the text within a program's window in Fluxbox?  ...for example the font in the menu bar (where it says "File    Edit   ...") in Firefox.  I've created styles that make the font size of everything outside the windows small, but then font sizes inside them look ridiculously large in comparison.  Is there a way to do this?

Thanks.

---

### Post by Spano on 2006-04-11
See if you have a .gtkrc-2.0 in your hidden home files. It probably reads something like this:

```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/daniel/.themes/marble-look/gtk-2.0/gtkrc"

include "/home/daniel/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```
If you do, and it does, then create a .gtkrc-2.0.mine file containing a line like this:
```
gtk-font-name = "helvetica medium 10"
```

Experiment with the font name and size untill you find something you like.
This will set a general font size for all your apps.  I think it might alter font size if you log back into Gnome or KDE.

---

### Post by antiemptyv on 2006-04-11
ahh, but i don't have either of those files.  and i'm not using gnome or kde; i'm using Fluxbox.

---

### Post by Spano on 2006-04-12
> I think it might alter font size if you log back into Gnome or KDE.
Understand your using Fluxbox.  The above was meant to warn you that creating a gtkrc.mine file as I suggested might mess with your fonts if you use multiple window managers.

I use Fluxbox on Ubuntu Breezy with rox as my file manager.  I had problems with fonts being too small in Rox and some of my other apps.  The FAQ on this page helped me solve those problems.
[http://rox.sourceforge.net/phpwiki/index.php/RoxFaq/Fonts](http://rox.sourceforge.net/phpwiki/index.php/RoxFaq/Fonts)
Read thru this page for some ideas.  Good luck and keep trying, Fluxbox is the BEST window manager.

---

### Post by antiemptyv on 2006-04-12
ok, so i figured it out--

running "startx" with the following switch: "-- -dpi 70" makes everything smaller relatively.

thanks to me.

---

