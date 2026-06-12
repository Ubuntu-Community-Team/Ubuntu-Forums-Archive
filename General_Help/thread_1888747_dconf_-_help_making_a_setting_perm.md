---
title: "dconf - help making a setting perm"
date: 2011-11-30
forum: General Help
---

### Post by Plasma_NZ on 2011-11-30
basically i know it can be done with gconftool - but those settings are different to dconf is seems... 

my goal 

/org/gnome/gnome-panel/layout "toplevel-id-list" set to []

by default when i login its set to 2 panels.. i want to remove those

im wondering what terminal command i can issue to change it.. 

e.g.
```

dconf --set /org/gnome/gnome-panel/layout/toplevel-id-list --type string "[]"

```
 - i know this doesnt work...

and i cannot find the place to do this in gconf-editor otherwise i would have used ```
 gconftool-2 --set /org/gnome/gnome-panel/layout/toplevel-id-list --type string "[]"
``` to do the setting...

---

### Post by Plasma_NZ on 2011-11-30
Ok... after some investigating... i see that gsettings is the equivilant of gconftool-2 

how can i use it to set the value of 

/org/gnome/gnome-panel/layout/toplevel-id-list 

to []

---

### Post by Plasma_NZ on 2011-11-30
Solved..

```

gsettings set org.gnome.gnome-panel.layout "toplevel-id-list" []

```

---

