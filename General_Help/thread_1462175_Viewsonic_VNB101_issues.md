---
title: "Viewsonic VNB101 issues"
date: 2010-04-25
forum: General Help
---

### Post by zb10948 on 2010-04-25
Hello people,

i'm having trouble with this netbook. The annoying problem is when i pull out the power cord, the damn thing suspends. "Smaller" issues are non-functioning bluetooth function key (BT radio always on, but i can do a script to signal poweroff to that particular USB device), and the processor (Atom 1.66) runs on 800MHz no matter if on cord or not. 

I've installed cpufreqd and cpufrequtils, edited configuration and now on cord it goes up to 1333MHz (i understand there is some sort of wide-known problem with this CPU, but i don't mind those 266MHz much...). However, after reboot, it stays again at 800MHz, cpufreqd is active, and the configuration remained same (!?)

Also, i had to put i8042.reset and i8042.nomux to get the keyboard and touchpad working...

---

