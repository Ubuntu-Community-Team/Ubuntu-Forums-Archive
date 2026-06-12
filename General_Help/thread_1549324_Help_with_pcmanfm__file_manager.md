---
title: "Help with pcmanfm  file manager"
date: 2010-08-09
forum: General Help
---

### Post by kut77less on 2010-08-09
How would I make pcmanfm draw the desktop instead of Nautilus?

---

### Post by Devi 710 on 2010-08-24
I don't know how to make PCmanFM the default file manager, but it is available through the 'Ubuntu Software Centre'. I am curious about this myself...

---

### Post by Devi 710 on 2010-08-24
Oh, I think I understand the question better now (I am no expert).

You might try:
```
pcmanfm -desktop
```

as the command in terminal. I believe the "-desktop" part is what you are looking for. I just read it here:

[http://blog.lxde.org/?p=727](http://blog.lxde.org/?p=727)

---

### Post by kerry_s on 2010-08-24
in gconf-editor-> desktop ->session -> required_components (i think)

replace nautilus with pcmanfm

---

