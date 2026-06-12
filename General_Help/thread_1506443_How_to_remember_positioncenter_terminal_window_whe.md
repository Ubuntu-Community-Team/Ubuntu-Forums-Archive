---
title: "How to remember position/center terminal window when opening it?"
date: 2010-06-10
forum: General Help
---

### Post by pstein on 2010-06-10
When I open a new terminal then it is alway put into the left upper corner.
 
How can I tell Ubuntu to open it at the last screen position when it was closed the last time?
 
Alternatively: How can I tell ubuntu to open it at least centered on the screen?
 
Peter

---

### Post by kaibob on 2010-06-11
I don't know how to do exactly what you want, but an alternative is to use the --geometry option. To see how this works, paste the following in a terminal window:

```
gnome-terminal --geometry=+200+150
```

If you want to include the window size:

```
gnome-terminal --geometry=75x25+200+200
```

If you want to use this method permanently, just modify the command in the launcher.

---

### Post by mal93 on 2010-10-20
Thanks i used 
```
gnome-terminal --geometry=75x25+350+330
```

and then modified the cammand in the porprieties and now it opens in the middle of the screen!

---

