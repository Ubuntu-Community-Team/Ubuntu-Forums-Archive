---
title: "Compiz/Metacity toggle problems"
date: 2010-08-01
forum: General Help
---

### Post by themanfromearth on 2010-08-01
After instaling Compiz Fuzion Icon, for turning off compiz to metacity, i have some problems. 
when i boot up, everything is runing fine, FPS counter is showing 59-60 FPS(never other numbers, always same, dunno why), but when i set metacity and revert back to compiz manager(throw Compiz "Fuzion Icon" menu), then FPS is 29-30(again never changes), and ofcourse poor graphics performance :( loging out doesnt help, only restart. Btw my card is Asus 8800GT(512MB, 235.65 driver), intel QuadCore Q6600, 4GB DDR2 1066Mhz, using ubuntu 10.04 x86.

Can any1 help me?

---

### Post by clhsharky on 2010-08-01
themanfromearth

> FPS counter is showing 59-60 FPS(never other numbers, always same, dunno why)
Should be correct for metacity compositor and vsync.

Compiz  has a 10% fps reduction in 3D on some apps and can be turned off.
Not 50% like in your case, your nv 8800 should easily handle the difference.

 Right click your Fuzion Icon, go down past your metacity/compiz switch, you should see a unredirect enable it. Its a compiz control for full screen 3D, Should help fps.

Sharky

---

### Post by themanfromearth on 2010-08-01
> **clhsharky said:**
> themanfromearth


Should be correct for metacity compositor and vsync.

Compiz  has a 10% fps reduction in 3D on some apps and can be turned off.
Not 50% like in your case, your nv 8800 should easily handle the difference.

 Right click your Fuzion Icon, go down past your metacity/compiz switch, you should see a unredirect enable it. Its a compiz control for full screen 3D, Should help fps.

Sharky

"go down past your metacity/compiz switch, you should see a unredirect enable it."

there is nothing there, just 2 options, indirect rendering, loose binding and select window decorato, only GTK window decorator listed, and nothing else.

---

### Post by clhsharky on 2010-08-01
themanfromearth

Sorry

indirect rendering - Compiz Fuzion Icon

unredirect - Compiz Control Center , main menu

Sharky

---

