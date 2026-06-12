---
title: "Remember DOS"
date: 2009-09-16
forum: General Help
---

### Post by triunenature on 2009-09-16
Here's what im looking for, have the labtop run without xserver, but on a moments notice run an app the requires xserver.

For example start in shell, just load firefox. and then once firefox quits, be right back in shell

Like, in dos, you start in "Console" and lets say you want to play your favorite game, warcraft.

find the file folder, the just type, war.exe

and Bam you have use of a mouse and your playing a game.

Now is there a way to do something like that in linux?

(Goal is super fast computer)

---

### Post by cmay on 2009-09-16
> **triunenature said:**
> Here's what im looking for, have the labtop run without xserver, but on a moments notice run an app the requires xserver.

For example start in shell, just load firefox. and then once firefox quits, be right back in shell

Like, in dos, you start in "Console" and lets say you want to play your favorite game, warcraft.

find the file folder, the just type, war.exe

and Bam you have use of a mouse and your playing a game.

Now is there a way to do something like that in linux?

(Goal is super fast computer)

yes there is sort of. I would suggest maybe using dwm.  I posted screenshot. I dont know if this is the sort of thing you are looking for.

---

### Post by Whiffle on 2009-09-16
> **triunenature said:**
> Here's what im looking for, have the labtop run without xserver, but on a moments notice run an app the requires xserver.

For example start in shell, just load firefox. and then once firefox quits, be right back in shell

Like, in dos, you start in "Console" and lets say you want to play your favorite game, warcraft.

find the file folder, the just type, war.exe

and Bam you have use of a mouse and your playing a game.

Now is there a way to do something like that in linux?

(Goal is super fast computer)


I think:
```
 xinit /usr/bin/firefox :0 
```

might do it.  You'll have to logout and stop gdm to do it.  

Also look into xinitrc and startx.

---

