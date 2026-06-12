---
title: "How to change the screen resolution??"
date: 2011-10-24
forum: General Help
---

### Post by rockager on 2011-10-24
hi forum!,

i want to increase my screen resolution to 1280x1024 from 1024 x 768 but every time i try the following commands the resolution changes to 1280x1024 but reverts back to 1024 x 768 after a restart :

```
xrandr --newmode  "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

xrandr --addmode VGA1 1280x1024_60.00

xrandr --output VGA1 --mode 1280x1024_60.00
```

(as instructed in this thread:  [http://ubuntuforums.org/showthread.php?p=8595940](http://ubuntuforums.org/showthread.php?p=8595940))

i also tried editing '/etc/gdm/Init/Default' as suggested in the above thread but the file does not open on ubuntu 11.10 (oneiric)

can anyone help??

---

### Post by dargaud on 2011-10-24
Can't you change it simply with the [System settings][Display and Monitors] ? If you have an nVidia graphic card, you should also use the [Nvidia X server setting], as root, and not forget to save the X configuration.

---

### Post by rockager on 2011-10-24
no. it still reverts back to 1024x786 after a restart

---

### Post by Grenage on 2011-10-24
If you have no luck with a startup script enabling the mode via xrandr (which should work), then a basic xorg.conf would work.

What's the make and model of your graphics card and monitor?

---

### Post by Angelus-Michael on 2011-10-24
[COLOR=RoyalBlue]***I had that problem too on an older version of ubuntu and I coudn't find an answer:(***[/COLOR]

---

### Post by CerberusCommand on 2011-10-24
What about installing **startup-manager** from the software centre and then changing the screen resolution from the software and then reboot and see if it has kept the settings.

---

