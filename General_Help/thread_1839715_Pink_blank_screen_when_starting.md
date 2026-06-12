---
title: "Pink blank screen when starting"
date: 2011-09-06
forum: General Help
---

### Post by jonny10 on 2011-09-06
I have Ubuntu installed on mini-pc of Zotac (ZBOX-ID41).
When turning the PC on and no mouse and no keyboard are connected, I'm getting blank pink screen. With no toolbars and no icons.

---

### Post by raja.genupula on 2011-09-06
are you able to move to terminal login 
ctrl+alt+f1

then stop your gdm and start again by using this . 

```
sudo /etc/init.d/gdm stop
```
```

sudo /etc/init.d/gdm start
```

let me know what you got

---

### Post by jonny10 on 2011-09-06
Didn't try "ctrl+alt+f1", since the problem happens without keyboard and mouse as mentioned.
Is the PC not supposed to start without keyboard and mouse?

---

### Post by raja.genupula on 2011-09-06
you need  A keyboard man , with out having keyboard we cant able to solve it (up to my idea )

---

### Post by jonny10 on 2011-09-06
will try later today, thanks

---

