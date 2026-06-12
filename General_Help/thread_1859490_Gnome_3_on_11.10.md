---
title: "Gnome 3 on 11.10?"
date: 2011-10-13
forum: General Help
---

### Post by galacticaboy on 2011-10-13
I know that Unity is built upon Gnome 3, but I would like to have the fallback mode that you get when you cant do Gnome shell. How can I get that? What do I have to install? Also will it install any programs? I don't want the programs, just gnome fallback.

---

### Post by BazookaAce on 2011-10-13
```
sudo apt-get install gnome-session-desktop-fallback
```

---

### Post by galacticaboy on 2011-10-13
> **BazookaAce said:**
> ```
sudo apt-get install gnome-session-desktop-fallback
```

Will that install all of those gnome programs like epiphany? I don't want those.

---

### Post by galacticaboy on 2011-10-13
> **BazookaAce said:**
> ```
sudo apt-get install gnome-session-desktop-fallback
```

I did that and got this
```
E: Unable to locate package gnome-session-desktop-fallback
david@David-Ubuntu:~$ 

```

---

### Post by galacticaboy on 2011-10-13
I found it, it was this:
```
sudo apt-get install gnome-session-fallback
```

---

### Post by CoreyB. on 2011-10-13
Do this

```
sudo apt-get install gnome-session-fallback
```

---

### Post by galacticaboy on 2011-10-14
> **CoreyB. said:**
> Do this

```
sudo apt-get install gnome-session-fallback
```

I did that and it worked! Thanks!

---

