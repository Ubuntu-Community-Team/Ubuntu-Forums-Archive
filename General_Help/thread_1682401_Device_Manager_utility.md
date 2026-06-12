---
title: "Device Manager utility"
date: 2011-02-05
forum: General Help
---

### Post by intoit on 2011-02-05
I'm looking for an app that will analyze my system and report similar to device manager. I'm trying to find out what type of ram i have installed (ddr 266/300/400 pc 2700/3200) etc.
 thanks in advance

---

### Post by Hakunka-Matata on 2011-02-05
search on "device manager" in synaptic.  Gnome has a version that works well.

---

### Post by stinkeye on 2011-02-05
In the terminal
```
sudo lshw -html > hardware.html
```
Will create a html file in your home folder which you can view 
in your browser.

---

### Post by intoit on 2011-02-06
it's stinkeye to the rescue. not exactly what i had in mind but the result is probably better.

thank-you

---

