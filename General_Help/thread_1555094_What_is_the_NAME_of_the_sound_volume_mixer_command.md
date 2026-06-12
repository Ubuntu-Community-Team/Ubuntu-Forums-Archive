---
title: "What is the NAME of the sound volume mixer command?"
date: 2010-08-17
forum: General Help
---

### Post by svref on 2010-08-17
For some reason my audio is really soft.

I can't find the way to the old gui mixer thing, y'know the one that has 75 useless sliders that all multiply together to give the output volume. I can't think of the command name. There's nothing in the applet except a simple slider.

**Can anyone tell me the name of this Gnomish mixer program?**

---

### Post by bigrayjr on 2010-08-17
Are you talking about alsa-mixer?  Or maybe it is alsamixer.

---

### Post by lidex on 2010-08-17
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

