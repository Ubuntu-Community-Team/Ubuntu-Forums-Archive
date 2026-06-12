---
title: "lxde bottom 'panel?' removed after second logins"
date: 2010-05-14
forum: General Help
---

### Post by Name141 on 2010-05-14
Hello, I installed lxde for my old P2 450 system but the er.. panel? I guess? Is removed where everything is.

Is there a way to get it back ? It happens everytime after the second login.


Even happened in 9.10 if I remember correctly. (I now have lucid).

For reference: [http://upload.wikimedia.org/wikipedia/commons/4/4c/LXDE_desktop_full.png](http://upload.wikimedia.org/wikipedia/commons/4/4c/LXDE_desktop_full.png) (the bottom thing with the clock, etc. )

---

### Post by kerry_s on 2010-05-14
:lolflag: ain't that a bitch, the run command is tied to the panel so you get stuck.
a) you can change the run command to a stand alone app, so you can relaunch the panel.
b) delete the settings profile for the panel, to set it back to default, hopefully that will fix whats killing it.
c) use a different panel, i used xfce4-panel in mine.


i noticed lxde seems to be going through an unstable faze right now, i was running lubuntu, so i just dropped it for straight openbox+xfce4-panel+netbook-launcher-efl, in other words custom.

---

### Post by Name141 on 2010-05-14
I just removed the folder inside of /home/user/lxde (or whatever)

and let it rebuild itself.

---

