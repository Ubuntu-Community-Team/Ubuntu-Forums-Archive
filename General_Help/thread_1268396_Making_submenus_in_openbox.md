---
title: "Making submenus in openbox"
date: 2009-09-16
forum: General Help
---

### Post by j33zU5 on 2009-09-16
I am just starting to use openbox, previously I was using fluxbox. I want to move Firefox, xchat, music and maybe more things to a submenu called apps. In fluxbox all I did was [submenu] (Apps) {} but I don't really get the whole xml thing yet.

---

### Post by Brandon Williams on 2009-09-16
To create a submenu, you just need to nest a new menu entity inside another one.
```
<menu id="openbox.menu" label="OpenBox Menu">
  <menu id="applications.menu" label="Applications">
    <!-- more submenus and/or menu items -->
  </menu>
</menu>
```

---

### Post by benj1 on 2009-09-16
theres also '<separator/>' (self explanatory)

also look up pipe menus (careful they just might be more addictive than conky)

---

### Post by j33zU5 on 2009-09-16
> **Brandon Williams said:**
> To create a submenu, you just need to nest a new menu entity inside another one.
```
<menu id="openbox.menu" label="OpenBox Menu">
  <menu id="applications.menu" label="Applications">
    <!-- more submenus and/or menu items -->
  </menu>
</menu>
```
Works great, thanks.

---

