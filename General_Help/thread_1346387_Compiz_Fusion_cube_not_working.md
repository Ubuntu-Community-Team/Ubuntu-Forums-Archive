---
title: "Compiz Fusion cube not working?"
date: 2009-12-05
forum: General Help
---

### Post by Rockanium on 2009-12-05
I have enabled all of the things that need to be enabled, i followed acouple of tutorials. but its still not working, i have set my graphics card to 'NVIDIA accelerated graphics driver (version 180)' wich is recomended have reset my computer many times.i set the visual effects to 'extra' and its still not working.

---

### Post by stinkeye on 2009-12-05
To see if compiz is running, install wmctrl
```
sudo apt-get install wmctrl
```
then in terminal run
```
wmctrl -m
```
which will tell you if compiz is running
eg```
Name: compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

If that checks out, in compiz config settings manager in..........[COLOR="DarkRed"]Edit:See next post to install if you don't have it.[/COLOR]
general options > desktop size  .... set the horizontal virtual size to 4.
Then check that you have 
enabled the plugins:
desktop cube
rotate cube

ctrl+alt+rightarrow should now rotate the cube.

---

### Post by amauk on 2009-12-05
the cube is not enabled by default
(a similar virtual desktop effect, "Desktop wall" is enabled by default instead)

Install the compizconfig-settings-manager
```
sudo apt-get install compizconfig-settings-manager
```
Then using the compizconfig-settings-manager (under System > Preferences) enable the cube (and if desired "rotate cube", "cube reflection and deformation" and "3d windows", which are plugins that enhance the cube)

---

### Post by plucky on 2009-12-05
> i set the visual effects to 'extra' and its still not working. 


Try setting visual effects to **Custom**

Good Luck

---

