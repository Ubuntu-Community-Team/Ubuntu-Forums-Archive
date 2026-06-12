---
title: "Disable middle click on R and L mouse input?"
date: 2006-05-03
forum: General Help
---

### Post by Grog140 on 2006-05-03
Is it possible to disable the setting that makes a middle click when you press the left and right mosue buttons together? I checked under Prefereced/Mouse but its not there. I cant think of anywhere else to find it. 

The reson I ask is that while running WoW in Wine I use the middle click to jump and press the Left and right mouse buttons to move forward. If I go to move forward I jump, and then remeain stationary.

Thanks

---

### Post by Ramses de Norre on 2006-05-03
sudo gedit /etc/X11/xorg.conf  search mouse section and set "emulate3buttons" to false.

---

### Post by Grog140 on 2006-05-03
Worked like a charm, thanks.

---

