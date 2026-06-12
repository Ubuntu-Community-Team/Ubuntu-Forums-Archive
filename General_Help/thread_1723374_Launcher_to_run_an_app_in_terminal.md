---
title: "Launcher to run an app in terminal?"
date: 2011-04-07
forum: General Help
---

### Post by HeroKing on 2011-04-07
i was wondering, and maybe hoping, if there was any way i can create a launcher to open a program that must be ran in terminal for it to run. i don't really like opening terminal and going to the program's location to launch it, so is there any way for this to work?

---

### Post by bodhi.zazen on 2011-04-07
use```
nohup gnome-terminal -e "full/path/to/command"
```

---

### Post by HeroKing on 2011-04-07
that doesn't seem to work. also forgot to mention this program needs to be ran as root, so i know i need to have gksudo somewhere in there

---

### Post by bodhi.zazen on 2011-04-07
> **HeroKing said:**
> that doesn't seem to work. also forgot to mention this program needs to be ran as root, so i know i need to have gksudo somewhere in there

gnome-terminal -e "gksu /path/to/command"

---

### Post by HeroKing on 2011-04-07
took me a while, but i finally got it. thanks a lot. switching to solved. though you put -c instead of -e and e was what i needed for this to work

---

### Post by bodhi.zazen on 2011-04-07
> **HeroKing said:**
> took me a while, but i finally got it. thanks a lot. switching to solved. though you put -c instead of -e and e was what i needed for this to work

Sorry about that, I edited my post.

Glad you got it working =)

---

