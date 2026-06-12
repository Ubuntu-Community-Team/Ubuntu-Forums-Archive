---
title: "How to switch my window manager back..."
date: 2006-04-15
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-15
I switched my wm to xfwm4 due to [ this ](http://ubuntuforums.org/showthread.php?t=102875&highlight=make+desktop) thread. I later found out that I can't use composite effects with my ATi Card. How can I change back to metacity (sp?) ?

---

### Post by trent dillman on 2006-04-15
```
sudo sed -i "s/openbox|xfwm4)/openbox)/" /usr/bin/gnome-wm
rm ~/.gnomerc
```

Don't get mad if anything goes wrong. I didn't test this...

---

### Post by CompShrink on 2006-04-15
Trent is right, but you also may have to:
 rm ~/.gnome2/session

to get it working.

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=CompShrink]Trent is right, but you also may have to:
 rm ~/.gnome2/session

to get it working.[/QUOTE]
Thanks. It worked.

---

### Post by trent dillman on 2006-04-15
No problem!!

---

