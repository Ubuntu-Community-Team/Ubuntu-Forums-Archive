---
title: "Locating installed programs"
date: 2009-09-03
forum: General Help
---

### Post by mervin on 2009-09-03
Forgive me if this is a dumb question. I've been using Ubuntu for a couple of years and this has been a niggling question throughout. I thought I'd ask in case I was creating work for myself!

When I install a new package through apt, is there any way to find the name of the program I need to run? Sometimes they are obvious, and tab completion is my friend. However, when the command is not the same as the package name and a link is not provided in the applications menu, I usually spend a while guessing/googling.

For example, I wanted to take a peek at packagekit. I installed "packagekit-gnome". It took me a fair while to figure out I needed to run "gpk-application". I couldn't find any information which specifically pointed me in this direction.

Is there some sort of apt functionality (something in apt-cache?) which will give me the command I need to run, or is it just trial and error?

---

### Post by Bachstelze on 2009-09-03
The command [font=monospace]dpkg -L <package name>[/font] will list all files installed by the package in question. Since most programs are installed in /bin, /sbin, /usr/bin or /usr/sbin, an obvious way to restrict the listing to installed programs is [font=monospace]dpkg -L <package name> | grep bin[/font].

---

### Post by CatKiller on 2009-09-03
```
dpkg -L* packagename*
``` (or Installed Files in Synaptic) will tell you which files are installed by a particular package. Files that are put in /usr/bin are conventionally executables that you can run.

EDIT: Curses! Beaten by HymnToLife :)

---

### Post by mervin on 2009-09-03
Excellent! I think this will save literally hours across my life.

Many thanks!

---

