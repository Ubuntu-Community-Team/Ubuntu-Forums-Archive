---
title: "places menu problem"
date: 2010-12-02
forum: General Help
---

### Post by amer-sa on 2010-12-02
hi i have a problem in places menu.here is an image .
can you help
new in ubuntu.
thx
[[IMG]http://img11.imageshack.us/img11/9600/problemri.jpg[/IMG]](http://img11.imageshack.us/i/problemri.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

when i click on them i get an error " could not open location " and " operation not supported "

and this too

[[IMG]http://img197.imageshack.us/img197/6285/screenshotr0.png[/IMG]](http://img197.imageshack.us/i/screenshotr0.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Habitual on 2010-12-02
Rebuild the gnome-panel...? *(NOTE) This will start with a NEW 'default' gnome-panel) You WILL lose all customization of same.

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by philinux on 2010-12-02
Places>Home Folder.

BookMarks> Edit Bookmarks. Just remove the ones you dont want.

---

### Post by amer-sa on 2010-12-03
> **Habitual said:**
> Rebuild the gnome-panel...? *(NOTE) This will start with a NEW 'default' gnome-panel) You WILL lose all customization of same.

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

am i gonna lose the shortcuts in the applications menu for the programs that I have already installed?

---

