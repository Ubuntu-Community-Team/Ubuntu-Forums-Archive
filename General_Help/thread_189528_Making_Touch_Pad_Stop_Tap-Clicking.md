---
title: "Making Touch Pad Stop Tap-Clicking"
date: 2006-06-05
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-05
does anyone know how to do this? its really getting annoying, like when I'm typing on my keyboard and I accidently hit the touch pad it completely messes me up... can anyone help? 

thanks

---

### Post by mscman on 2006-06-05
OK, try this.

Open a terminal and make a backup of your xorg.conf file by typing
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

Then edit the file using
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to the section about your Synaptics touchpad and change the line about MaxTapTime to read 
```
Option "MaxTapTime" "0"
```
If this line doesn't exist at all, go ahead and add it.

---

### Post by andrejkw on 2006-06-05
Hey,
I think I know the solution to your problem.

Inside your **/etc/X11/xorg.conf**, find this section:
```

Section "InputDevice"
    Identifier "Synaptics Touchpad"
    .... SOME STUFF HERE ....
EndSection

```

Right on a line before **EndSection** add **Option      "MaxTapTime" "0"**.
Which should make it look like:
```

Section "InputDevice"
    Identifier "Synaptics Touchpad"
    .... SOME STUFF HERE ....
    Option      "MaxTapTime" "0"
EndSection

```

Good luck! :)

---

### Post by Patrick-Ruff on 2006-06-05
thanks guys worked perfectly.

---

