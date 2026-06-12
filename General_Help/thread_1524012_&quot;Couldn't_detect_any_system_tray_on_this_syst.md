---
title: "&quot;Couldn't detect any system tray on this system&quot;"
date: 2010-07-04
forum: General Help
---

### Post by koekjestrommel on 2010-07-04
[IMG]http://i273.photobucket.com/albums/jj202/k0ffiekopje/Screenshot-15.png?t=1278271043[/IMG]
Programs like aMSN, and controlling music volume, etc are gone in the upper-taskbar/panel. I think I accidentally managed to delete the whole upper panel, and created a new one. Still the programs I start up which suppose to appear in the upper panel, don't appear there. Any idea how to fix this, or to add those functions to the upper panel?

Cheers,

Joost

---

### Post by J V on 2010-07-04
rightclick the panel and select "Add to panel" followed by "Notification area"

---

### Post by koekjestrommel on 2010-07-04
Works thanks, but I still don't know how to change the music volume, or how to add that function. Thank once again :)

---

### Post by J V on 2010-07-04
Same thing, only add indicator applet :)

---

### Post by koekjestrommel on 2010-07-04
Works like a charm, thank you ^^

---

### Post by Leppie on 2010-07-04
you could also use this command to restore the panel to its original state:
```
gconftool-2 --recursive-unset /apps/panel | killall gnome-panel

```

zijn jullie beiden Nederlanders?

---

