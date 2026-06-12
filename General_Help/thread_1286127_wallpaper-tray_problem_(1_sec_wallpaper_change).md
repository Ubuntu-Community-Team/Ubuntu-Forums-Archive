---
title: "wallpaper-tray problem (1 sec wallpaper change)"
date: 2009-10-08
forum: General Help
---

### Post by inder.vs on 2009-10-08
i accidently set the time of wallpaper to 1 sec in prefrences. now the panel is frozen and the speed of pc is very very slow when it is running.  i tried to reinstall the wallpaper-tray but the problem continues when ever i start the wallpaer-tray. is there any way to solve this. 

plz   help.

---

### Post by alphaniner on 2009-10-08
If you installed it through Synaptic or aptitude, try removing it with **purge**:

```
sudo apt-get purge wallpaper-tray
```

Then install fresh.  Removing with **purge** removes configuration files that can remain if you use **remove** or **re-install**.

---

### Post by inder.vs on 2009-10-09
sorry to inform you that the problem still continues. 

i am new to linux. is there any way that the file which is storing the configuration can be edited.

---

### Post by inder.vs on 2009-10-09
problem solved .

i changed the setting by going to home folder , then press "ctrl + h  " then go to .gconf. then app then wp_tray . now open %config with text editor and change the time to any number except "0" (zero) .

have a great day to all.

---

