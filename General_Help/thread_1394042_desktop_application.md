---
title: "desktop application"
date: 2010-01-30
forum: General Help
---

### Post by r_s on 2010-01-30
I want to put a script of mine in the applications menu , so that when I click on it , it executes itself ...so I created a new application by the name myapplication.desktop in /usr/share/applications/  . But when in GUI mode I traverse down to this directory and click on myapplication.desktop . It gives me an error "myapplication.desktop is not a directory".
The crazy part is that when I run it using the terminal ...
freedom@freedom-laptop: /usr/share/applications$ myapplication
it runs perfectly well.
I can't understand the problem...the script is correct , but I don't know about the error saying "it is not a directory" as all the other files in there are also files and they do run even in graphical mode .

---

### Post by PeEllAvaj on 2010-01-30
I don't think you are supposed to put the application in /usr/share/application/, this is supposed to just be the desktop file and metadata which points to the application.

I just made an ubuntu game, and my .desktop file ended up looking like this:

```

[Desktop Entry]
Type=Application
Name=HexSLayer
GenericName=HexSLayer Tile Game
Comment=Win the game by conquering territory and taking over the whole map
Icon=hexslayer
Exec=hexslayer
Terminal=false
Categories=Game

```

This file then ends up running /usr/games/hexslayer, which is also in PATH.

Does that make sense? I could be way off, as this is my first .desktop file as well.

---

