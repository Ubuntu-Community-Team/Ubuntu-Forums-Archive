---
title: "zsh not working right"
date: 2011-05-20
forum: General Help
---

### Post by joshuachoo on 2011-05-20
Okay, I installed zsh, created a .zshrc file in my home directory, and set zsh to be my default using :
```
chsh -s /bin/zsh $USER
```However, when I launch my terminal (gnome-terminal), I seem to get zsh without having read my .zshrc file.

It only shows:
```
$
```
 
```
echo $SHELL
```
When I try the above command, it shows me:
```
/bin/sh
```

Furthermore, if I run zsh manually then it reads *.zshrc* and works right. What's wrong with zsh?

---

### Post by gmargo on 2011-05-20
Log out of the desktop, and log back in.  (Or reboot if using auto-login.)  Then a new gnome-terminal will use **zsh(1)**.

---

### Post by joshuachoo on 2011-05-21
Yeah, I just realized that. Thanks. They do not often mention that on tutorials.

---

