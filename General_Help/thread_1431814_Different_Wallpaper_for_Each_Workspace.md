---
title: "Different Wallpaper for Each Workspace?"
date: 2010-03-17
forum: General Help
---

### Post by madmax.santana on 2010-03-17
I am using Ubuntu 8.10... 

Is there a way to keep a separate wallpaper for each workspace???

---

### Post by darolu on 2010-03-17
The only way I know is to do it via compiz. Open CCSM and go to Wallpapers and select your wallpapers, then press ALT+F2 and execute "gconf-editor", go to apps-nautilus-preferences and uncheck the "show_desktop" option.

This will disable icons on your desktop though.

If you don't have CCSM install it with (in a terminal):
```
$ sudo apt-get install compizconfig-settings-manager
```
To summon it, press Alt+F2 and run: "ccsm"

---

### Post by madmax.santana on 2010-03-17
Nah... The desktop icons tradeoff is not acceptable... :)

Any other solution?

---

### Post by Jeff Anthony on 2010-03-17
Would it be acceptable if you simply changed the way you access those shortcuts? I might suggest using a drawer or similar menu device for keeping your "desktop" shortcuts.

---

### Post by linden940 on 2010-03-17
hmm this would be something nice to have added to the desktop...but as far as i know...no you can not do so 

(u can do what the one guy said..but other than that..no it wont work)

---

### Post by Drone4four on 2010-04-18
I found this thread through a search for "disable icons".  It has proven useful to me.

---

### Post by Drone4four on 2011-05-21
Now I wonder: How do I remove all the icons on the XFCE desktop?

---

