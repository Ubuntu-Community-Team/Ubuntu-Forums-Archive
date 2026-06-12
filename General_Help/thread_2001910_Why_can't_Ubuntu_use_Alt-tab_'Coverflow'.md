---
title: "Why can't Ubuntu use Alt-tab 'Coverflow'"
date: 2012-06-11
forum: General Help
---

### Post by Hazzabin on 2012-06-11
Ok I know it's only 'eye-candy' stuff, but I'm failing to see why Cinnamon and Zorin can have it, but Ubuntu does Not.
If there is a way of implementing this please let me know.

oh yes the extension in Gnome extensions does not work no more

regards
Hazz

---

### Post by zombifier25 on 2012-06-11
Ubuntu has it for a very long time now, as a Compiz effect. Just install the extra effects and cccsm:
```
sudo apt-get install compiz-plugins-extra compizconfig-settings-manager
```
Then open ccsm, enable Shift Switcher, click on it and map the "Next Window" buttons,... to whatever you like. Note that Alt-Tab will conflict with Unity's existing windows switcher and ccsm should warn you about that. Just choose to disable the Unity one.

---

