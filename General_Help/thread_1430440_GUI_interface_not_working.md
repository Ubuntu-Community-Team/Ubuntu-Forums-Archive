---
title: "GUI interface not working"
date: 2010-03-15
forum: General Help
---

### Post by RACazorla on 2010-03-15
H, I'm not able to get into the GUI interface, what happed was that I tried connecting an LCD to the laptop and try to auto detect it, after it asked me if the display looked OK and I answered keep current config. The screen on the Laptop just garbled and could not see anything so I restarted the Laptop and since then I'm only able to get to the Text interface and not to gnome.
I've already tried
startx just sent me an error msg to check on var/logXorg.0.log which I'm attaching
sudo dpkg-reconfigure -phigh xserver-xorg  no luck there :icon_frown:
sudo apt-get install xserver-xorg which only told me I was up to date :-k

any ideas? Help

---

### Post by solar george on 2010-03-15
Have you tried simply rm-ing your xorg.conf
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by RACazorla on 2010-03-15
> **solar george said:**
> Have you tried simply rm-ing your xorg.conf
```
sudo rm /etc/X11/xorg.conf
```
Thank you it worked :D

---

