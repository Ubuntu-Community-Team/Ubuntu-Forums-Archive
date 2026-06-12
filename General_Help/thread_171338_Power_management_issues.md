---
title: "Power management issues"
date: 2006-05-06
forum: General Help
---

### Post by tsb on 2006-05-06
I have no options in power preferences-options
I just want to make my laptop automatically shutdown if the power is below 3%
it was so easy to do in Kubuntu, butI can't figure it out in Ubuntu
I tried to install gnome-screensaver, but it had virtually nothing.....the default screensaver has the advanced menu with the DPMS so I uninstalled gnome-screensaver and left the default
power preferences gives me an error that gnome-screensaver doeasn't have DPMS enabled
do I need to uninstall the default before installing gnome-screensaver?
why do I have no options in power preferences-options?
also, how do I make the screensaver stop when the diplay goes on standby like it did in Kubuntu?
thanks.

---

### Post by tsb on 2006-05-06
bump

---

### Post by tsb on 2006-05-07
bump

---

### Post by nanotube on 2006-05-08
did you try installing package "gnome-power-manager"? give it a shot, run
```
sudo apt-get install gnome-power-manager
```
from a terminal. then try playing with your settings through it.

---

### Post by Anilkumar on 2006-05-08
we can do it in gnome also but now i am not in linux .you can from preferences in system->screensaver->there u have power mangement

---

