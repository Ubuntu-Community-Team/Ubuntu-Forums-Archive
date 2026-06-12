---
title: "Remove top panel classic natty"
date: 2011-05-14
forum: General Help
---

### Post by Essential on 2011-05-14
Hey. Since upgrading to 11.04 I've been trying to remove the top panel in classic in the same manner as I did with 10.10.

gconf-editor -> desktop -> gnome -> session -> remove "gnome-panel" value.

This does not remove the top panel anymore. Relog and restart has been tried. Does anyone have any suggestions on how to remove it? I'm using AWN, so the top panel isn't useful for me :)


Solved: So I just randomly thought of changing my login session to user defined, and voila! Panel gone :) Guessing logging into classic just won't let you log on without it.

---

### Post by JOHNNYG713 on 2011-05-14
Right click top panel and remove this panel !

---

### Post by kerry_s on 2011-05-14
> **Essential said:**
> Hey. Since upgrading to 11.04 I've been trying to remove the top panel in classic in the same manner as I did with 10.10.

gconf-editor -> desktop -> gnome -> session -> remove "gnome-panel" value.

This does not remove the top panel anymore. Relog and restart has been tried. Does anyone have any suggestions on how to remove it? I'm using AWN, so the top panel isn't useful for me :)

put avant-window-navigator in stead of leaving it blank. you can then turn off auto start in avant preferences.

---

### Post by kerry_s on 2011-05-14
> **JOHNNYG713 said:**
> Right click top panel and remove this panel !

doesn't work when you want to totally remove all gnome-panel's.

---

### Post by hawthornso23 on 2011-05-14
You'd be better off trying this in Ubuntu classic. Unity sometimes reacts in a most unladylike fashion when attempts are made to reconfigure her.

---

### Post by Essential on 2011-05-14
Hey again. I've tried putting avant-window-navigator in stead of gnome panel, no resuls :/ 


Here's a pic of my settings (note that there's no values there now though). I've tried relogging with both values empty, with avant-window-navigator etc.

[http://bildr.no/view/882786](http://bildr.no/view/882786)

---

