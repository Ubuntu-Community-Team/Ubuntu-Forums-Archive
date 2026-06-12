---
title: "why is getting a dock this hard?"
date: 2009-09-19
forum: General Help
---

### Post by wcutrombonekid on 2009-09-19
i have been looking around for over an hour and can't seem to find anything.

i want to get a dock like what macs have at the bottom of their screen.  I know they exist, i've seen them.  I may be searching for the wrong thing in synaptic but i'm not sure.  I'm running Jaunty and can't seem to find it.  Maybe i'm dumb.  Could someone please point me in a good direction for this.

thanks

---

### Post by NoaHall on 2009-09-19
First, make sure your drivers are installed, and compiz is running

(sudo apt-get install compiz)

Then, run 

sudo apt-get install avant-window-navigator

Then to turn it on, Applications -> Accessories -> Avant

---

### Post by CatKiller on 2009-09-19
```
sudo apt-get install avant-window-navigator
```

---

### Post by nothingspecial on 2009-09-19
```
sudo apt-get install gnome-do avant-window-navigator cairo-dock
```

Have a go with them all and remove the 2 you don`t want.

---

### Post by wcutrombonekid on 2009-09-19
thank you, no where had i read that i needed compiz installed to do that (now that i think if it, it makes sense though.)  appreciate it guys!

---

### Post by jocko on 2009-09-19
> **wcutrombonekid said:**
> thank you, no where had i read that i needed compiz installed to do that (now that i think if it, it makes sense though.)  appreciate it guys!
You don't need compiz to have a dock, but at least awn require some form of compositing (so activating metacity compositing would be enough). Afaik cairo-dock does not require compositing.

---

