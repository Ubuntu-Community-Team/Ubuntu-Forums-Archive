---
title: "How to add a directory to the menu without using a GUI?"
date: 2010-10-02
forum: General Help
---

### Post by _sluimers_ on 2010-10-02
[IMG]http://i53.tinypic.com/2rfcxs7.png[/IMG]

I'm trying to make my package install menu items. Now I know how to add desktop items to the menu, but when I try adding a directory to /usr/share/desktop-directories, nothing happens. Here's what I've tried, the result is that the desktop file shows upin the "Other" Category while the directory doesn't show at all:

/usr/share/desktop-directories/ika.directory

```

[Desktop Entry]
Name=Ika
Comment=Ika Directory
Type=Directory
Icon=ika

```


/usr/share/applications/ika-winter.desktop

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Icon[en_US]=ika-game
Exec=ika /usr/share/ika/ika-games/Brickfall
Name[en_US]=Brickfall
Name=Brickfall
Comment= A columns like game
Icon=ika-game
Categories=Ika;

```
/usr/share/desktop-directories/ika-winter.desktop
 
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Icon[en_US]=ika-game
Exec=ika /usr/share/ika/ika-games/Winter
Name[en_US]=Winter
Name=Winter
Comment=RPG game
Icon=ika-game
Categories=Ika;

```



Why is this?

---

### Post by dino99 on 2010-10-02
right click on "Applications" in the menu bar, check "edit menu", then a gui popup where you can select a directory and add a new menu .
With nautilus, you can create a new directory, give it a name then drag and drop it to attach it on an other dir

---

### Post by _sluimers_ on 2010-10-03
>  right click on "Applications" in the menu bar, check "edit menu", then **a gui pops up** where you can select a directory and add a new menu .
With nautilus, you can create a new directory, give it a name then drag and drop it to attach it on an other dir 

This can't be the answer. I'm not asking how to add them manually via a GUI. I know how to do that and that works fine. 
I'm asking for a way to add these the same way wine does and for some reason my attempt is not working. They don't show up at the correct places or at all.

I also can't find my manually added menu items that do work anywhere in nautilus.

[EDIT] I'll change the title because it looks misleading [/EDIT]

---

### Post by _sluimers_ on 2010-10-04
I solved it it! I needed an additional .menu file placed in /etc/xdg/menus/applications-merged (shamelessly copied the contents from wine-wine.menu and edited to suit my needs).
[http://standards.freedesktop.org/men...t/ar01s02.html](http://standards.freedesktop.org/men...t/ar01s02.html)

---

