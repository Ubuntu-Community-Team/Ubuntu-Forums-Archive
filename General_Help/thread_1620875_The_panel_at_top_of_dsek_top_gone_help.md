---
title: "The panel at top of dsek top gone help"
date: 2010-11-13
forum: General Help
---

### Post by 340six on 2010-11-13
The default one at the top had a problem as the log out would come and go leaving me no way to turn off.
I thought I was just doing a simple deletion of my name but the whole thong is gone

---

### Post by Verbeck on 2010-11-13
do you have a bottom panel? if so, right click it and select 'new panel'. if an empty space appears on the top, then open a terminal (alt+ctrl+T) and enter the command ```
*killall gnome-panel*
```

---

### Post by choochoousmc on 2010-11-13
in the upper panel (where it would be) right click it.
New window opens scroll down to main menu bar. click add.
It should be back.
You might have to do from live cd. Not sure. Had to do it once about 6 months ago.
You can also do it from a terminal window. But don't know the command or how to get to it with panel gone.

---

### Post by 340six on 2010-11-13
I added a new panel have it almost like it was, added to it to get the blank panel  
The circle "main menu"  "firefox" "printer icon" "time/ date" and the shut down that was missing in the original panel.
How do i get  **Applications, Places and System back** they are listed in main menu

---

### Post by Swagman on 2010-11-13
To rebuild the top panel back to original state Copy & paste this in a terminal

```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```


If you ever lose the shutdown button then click left alt & F2 and enter sudo halt

---

### Post by 340six on 2010-11-13
> **Swagman said:**
> To rebuild the top panel back to original state Copy & paste this in a terminal

```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
If you ever lose the shutdown button then click left alt & F2 and enter sudo halt
thanks that did the trick.
Why does the shut down icon keep going away?:confused:

---

### Post by Swagman on 2010-11-13
> **340six said:**
> thanks that did the trick.
Why does the shut down icon keep going away?:confused:

Dunno but it IS annoying aint it. It seems to lose a few pixels from the right of the screen

---

### Post by 340six on 2010-11-13
Yes it is a pain
The only way to turn it off was shut the power off to the computer.
As of today I right clicked the panel and added another one

---

### Post by kakila on 2010-11-16
I had the same problem,
running 
gnome-panel

was producing 

gnome-panel: error while loading shared libraries: /usr/lib/libgnutls.so.26: invalid ELF header

Reinstalling the libraries from synaptic solved the problem of the missing panels. However, now I get an error at startup

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

---

