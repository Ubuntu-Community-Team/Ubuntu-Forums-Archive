---
title: "blank desktop (no unity) ubuntu 11.04"
date: 2011-07-10
forum: General Help
---

### Post by jan-90 on 2011-07-10
So i was messing with the package that controls features such as window wobble and many other visual effects (advance desktop by compiz i think).
anyway i accidentally disabled unity and now i only have a blank desktop. ctrl alt T does not work, however i can open the terminal by right click cread launcher "gnome-terminal"

now i need to reset the setting to the original ubuntu (those on install) 
how can i do this with only access to terminal. as u might have noticed am a huge ubuntu noob so please keep that in mind.

thanks

---

### Post by macaholic on 2011-07-10
You can try running```
unity --reset
``` in the terminal. That *should* reset Unity's settings to the defaults.

Anoher thing you could try is to run```
ccsm
``` Then go into Preferences and hit "Reset to defaults".

---

### Post by jan-90 on 2011-07-11
Anoher thing you could try is to run```
ccsm
``` Then go into Preferences and hit "Reset to defaults".[/QUOTE]

this did the trick
thanks! i googled the command to open up the prog but to no avail

---

