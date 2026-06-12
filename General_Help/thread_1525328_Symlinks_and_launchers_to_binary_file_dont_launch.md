---
title: "Symlinks and launchers to binary file dont launch"
date: 2010-07-06
forum: General Help
---

### Post by Lolpanda on 2010-07-06
Hey guys, Installed UT2004 (i know, old, but thats one of the best, so...shush :P)

If I go into ~/Games/UT2004/System/    (I wanted it to be in my home directory so I had read/write without any hassles)

and doubleclick the "ut2004-bin-linux-amd64" file, UT loads up perfectly 

But if I create a symlink to it and put it in ~/Games, or if I create a Gnome Menu launcher for it and put it in the menu and double try to click either the link or the launcher..nothing happens. 

Is there some special command I have to put infront of the gnome launcher command / symlink for it to open a binary file?

Right now the gnome-menu launcher command line just says "/home/eric/Games/UT2004/System/ut2004-bin-linux-amd64"  done.

---

### Post by Lolpanda on 2010-07-06
solved haha, the variables with the launcher didn't get configured correctly during install, just had to change them myself

---

