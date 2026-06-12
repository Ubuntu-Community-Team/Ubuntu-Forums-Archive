---
title: "[Help] How 2 PrtSc (Print Screen) ?"
date: 2010-01-30
forum: General Help
---

### Post by retro_killa on 2010-01-30
How can I take a screen shoot of the taskbar/program & nothing ells ? 

For window users such as XP/Vista if you do not want to capture the entire screen, Select the window you wish to capture and Hold Down the ALT key while simultaneously pressing the Print Screen button.  This will capture ONLY the selected Windo

But how can I do this with Ubuntu ? I would like to take screen shoots of the taskbar by its self & a few programs with having any backgrounds int he image.

---

### Post by howefield on 2010-01-30
Press the alt key along with the printscreen to take a shot of the active window.

---

### Post by retro_killa on 2010-01-30
> **howefield said:**
> Press the alt key along with the printscreen to take a shot of the active window.

but what about jsut doing the taskbar ? or calculator with out having in background image or active windows ?

---

### Post by howefield on 2010-01-30
Don't know about the taskbar, but single applications is alt + printscreen.

---

### Post by howefield on 2010-01-30
You can do it with imagemagick. I was trying it a few days ago.


Try this, open a terminal (Applications > Accessories > Terminal) and type the following.

```
import screenshot.jpg
```

press enter and then click and drag your left mouse button over the area you want for the screenshot.  

You'll find the jpg in your home folder.

---

### Post by hemimaniac on 2010-01-30
Menu > Accessories > Take Screen Shot

then you can pick whole screen, active desktop, selected area, and with or without mouse

---

### Post by retro_killa on 2010-01-30
> **howefield said:**
> You can do it with imagemagick. I was trying it a few days ago.


Try this, open a terminal (Applications > Accessories > Terminal) and type the following.

```
import screenshot.jpg
```

press enter and then click and drag your left mouse button over the area you want for the screenshot.  

You'll find the jpg in your home folder.

Thank you this worked out very well I went ahead & did this 
```
import screenshoot.png
``` 

turned out to do just what I wanted but I wish there was a better way. Thanks !!! 

> **hemimaniac said:**
> Menu > Accessories > Take Screen Shot

then you can pick whole screen, active desktop, selected area, and with or without mouse

Thank you but I am looking to take images with out background. I would like just the application/folder or task bar nothing ells but thansk for this idea ;)

---

