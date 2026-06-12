---
title: "help!"
date: 2006-03-04
forum: General Help
---

### Post by drop_d33 on 2006-03-04
ive just attempted to enable my nvidia Ge5200 on ubuntu.. when i pressed ctrl+alt+backspace on the terminal to check if it was successfull, the screen went black. even if i reboot, the screen is still blank. i forgot the link that had the steps i followed, which told me to press Ctrl+al+backspace.. how can i fix this?!!

---

### Post by dermotti on 2006-03-04
hit cntrl + alt + F3

login

sudo vi /etc/X11/xorg.conf

finde driver "nvidia" and change to "vesa"

then startx or reboot

---

### Post by dermotti on 2006-03-04
At least then you will have a GUI.....you will have to research more how to get nvidia to work.

---

### Post by Ramses de Norre on 2006-03-04
And please put the subject of your post in the title, it gets pretty annoying when everyone calls his threads 'help' or 'problem'.

---

### Post by akiro.yamamoto on 2006-03-04
I would use nano, I think it's more newbie friendly :)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
sudo nano /etc/X11/xorg.conf

```
Then find "nvidia" and replace it with "nv".

Are you sure that you used the correct drivers?
Some have reported having better results with the nvidia-glx-legacy drivers.

---

