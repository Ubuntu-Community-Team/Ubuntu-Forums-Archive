---
title: "can't remove empathy"
date: 2010-01-03
forum: General Help
---

### Post by Liso22 on 2010-01-03
I installed Ubuntu today and I have to say it's awesome, shortly after trying it I decided to remove XP, I had some problems I could solve myself but right now my "biggest" one is that I can't uninstall empathy, it may sound stupid but I totally need to take it out, I installed Pidgin and it works like a charm btw: I removed empathy from the ub soft center but it didn't change anything

I had a lot of questions but I resolved all of them in the middle of this post (= I have another question but it isn't as important, does anyone know how to set up the cube? I'm sure I'll end up turning it off but I want to try it, thanks

---

### Post by nikhilbhardwaj on 2010-01-03
try removing it
using the synaptic package manager

you'll find it under System>Administration

---

### Post by todak on 2010-01-03
```
sudo aptitude purge empathy
``` will do the trick. Then go to your home folder and enable hidden files by pressing Ctrl+h. Remove the .empathy folder.

---

### Post by Liso22 on 2010-01-04
thanks a lot I could remove it after doing that and reseting

---

### Post by Marrkk on 2010-01-04
make sure removing it doesn't  remove anything else you want !

---

