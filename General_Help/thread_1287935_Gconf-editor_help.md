---
title: "Gconf-editor help"
date: 2009-10-10
forum: General Help
---

### Post by sports fan Matt on 2009-10-10
I had a thread several months ago about having my "home folder" on my desktop, but I cant remember where the setting is in gconf-editor to not have it on my desktop...Anyone know?

---

### Post by drs305 on 2009-10-10
If you mean not show home on the Desktop, it is at
```

gconftool-2 -s -t bool /apps/nautilus/desktop/home_icon_visible false

```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by mick55 on 2009-10-10
hi sox fan

Are you familiar with "Ubuntu Tweak" ?
It's in the repositories and it allows you to tweak many 
settings.Home folder as desktop is one of them.
Conveniently it is located under the "desktop" tab.

Makes changing basic settings really simple.

Cheers
mick

---

### Post by mc4man on 2009-10-10
The other possibility , (your weren't exactly clear in op) is
```
gconftool-2 -s -t bool /apps/nautilus/preferences/desktop_is_home_dir false

```

---

