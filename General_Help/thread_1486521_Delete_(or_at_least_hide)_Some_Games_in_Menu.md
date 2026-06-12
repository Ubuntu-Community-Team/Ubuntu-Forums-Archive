---
title: "Delete (or at least hide) Some Games in Menu"
date: 2010-05-17
forum: General Help
---

### Post by klausner on 2010-05-17
There are a number of games that *force* their way onto the applications menu, even if they are unchecked. e.g. Iagno, Nibbles, Robots, etc. I can't delete them from the games menu, and I haven't been able to identify them as belonging to a particular package. FWIW, I do **not** have gnome-games installed.

Is there a way to hide/delete/uninstall these?

---

### Post by todak on 2010-05-17
Just uninstall them individually, e.g., ```
sudo apt-get remove robots
```

---

### Post by solitaire on 2010-05-17
or right click on "Applications" and select "Edit Menus"
there you can delete items from the menus.

---

### Post by klausner on 2010-05-17
> **todak said:**
> Just uninstall them individually, e.g., ```
sudo apt-get remove robots
```

Except there is no *robots* package. Nor any of the others. Nor can I identify them as part of *any* package except gnome-games, which isn't installed.

---

### Post by klausner on 2010-05-17
> **solitaire said:**
> or right click on "Applications" and select "Edit Menus"
there you can delete items from the menus.

Except I already said they CAN"T be deleted from the menu. Press delete, and nothing happens.

---

### Post by todak on 2010-05-18
Use Software Center and do a search for each game, using their menu names, i.e., Robots, Nibbles, etc. If it is installed, you will be shown the option to remove the game.

---

### Post by Ravey on 2010-05-18
Try reinstalling gnome-panel in synaptic if you can't hide things on the menu.

---

### Post by Rubi1200 on 2010-05-18
Trying to remove individual games from the menu does not work. Removing via Synaptic or apt may not be a good idea because so many things are inter-connected in Ubuntu.

My solution:

left click on the panel to edit menus, remove the entire Games entry.

If you then want to play individual games afterwards use Alt+F2 and type the name of the game to start it e.g. Alt+F2 and type Gnometris will start the game for you.

---

### Post by akakingess on 2010-05-18
I just right-click and chose to edit menu, then rather than just unchecking "robots" I right-clicked and deleted it and now it no longer appears in the menu. Don't know if that is just not working for you or not, but I was able to get rid of it rather easily.

Don't know if this helps but they are located at /usr/games/ ...

---

### Post by klausner on 2010-05-24
The problem turns out to be that the Gnome menu won't delete entries for packages that aren't installed. When I did a clean install of lucid, it didn't install gnome-games. But I had menu entries still there from karmic, since I saved the /home partition.

Installed gnome-games, uninstalled it, and got rid of the phantom entries.

---

### Post by icemonsta on 2010-12-07
I found an easy solution for this.

When looking at this issue, I found I was unable to hide top level items, such as the games folder.

Solution: Create a folder at top level, call it something like "Hide games" and move the games folder inside the hide games folder. Then you can uncheck the checkbox for showing the games folder. Games = Gone :D

---

### Post by klausner on 2010-12-07
Well if you want to waste space and use a kludge......

---

### Post by Megaptera on 2010-12-08
Thanks icemonsta, I might use that.

---

### Post by nubuuz on 2011-10-05
nice that reinstall fixed it for you, klausner.

i've got a clean install of 11.04 (but running classic instead of unity) 
and unselected all these prepackage games in main menu/games and still they wouldn't go away!

(i'm not saying i want to completely remove the games, nor the entire game menu, etc.)
(just don't want to look at stuff that i rarely use, all the time...)

even my ~/.config/menus/applications.menu indicates games like gbrainy, soltaire, mahjongg, quarry, rhino as "excluded" but they still show up.

but it further includes a directory from ~/.local/share/applications where gbrainy.desktop has a file with the line:

NoDisplay=true

changing that to 

NoDisplay=false

will remove the applications menu entry without even rebooting!

sol.desktop, on the other hand, doesn't even have that line, but adding it still works to remove it from the menu.

the other games don't even have files in this directory, 
but copying gbrainy.desktop (with the changed line, and replacing the relevant name information, 
if you feel like it) to 

gnomine.desktop
grhino.desktop
mahjongg.desktop

takes them out of the menu. 
(re)moving these files brings the entries right back.

hopefully, at some point, i'll get a little script to generate these files, 
and force my menus to be the way that I want them, overruling wherever is overruling my preference selections.

---

### Post by Rubi1200 on 2011-10-05
Thread closed.

Reason: necromancy

---

