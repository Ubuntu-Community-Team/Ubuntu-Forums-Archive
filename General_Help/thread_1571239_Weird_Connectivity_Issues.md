---
title: "Weird Connectivity Issues"
date: 2010-09-09
forum: General Help
---

### Post by motleycrew on 2010-09-09
Perhaps someone can shed some light on a very frustrating issue. I cannot connect to the internet wirelessly any longer. I installed 10.4 the day it came out and everything worked great right out of the box until a few days ago. I dual boot my Toshiba laptop with Vista 32bit and I can connect to my router wirelessly in Windows and I can use the eth0 connection without any problems in Ubuntu. The only thing I cannot do is connect to the router with a wireless connection. I have another laptop that runs XP and I do not have any connection issues there either. This is a problem with setting in Ubuntu alone. I have tried everything but I must be overlooking something. I look at network properties and I see lo and eth0 but not wlan0. Nothing changed, it just stopped working! Well, I did load RISK with WINE to play but I can't believe it could change wireless connectivity changes?

---

### Post by motleycrew on 2010-09-09
***SOLVED***  

Maybe this will help someone else...

After further investigation, I discovered that from the time I installed 10.4, I never had the 'notification tray' activated in the panel..I always wondered why I never had a battery health icon or a connection icon..anyway, I added it to the panel and I went to wireless connections and found my router and entered the key and I'm golden..Perhaps the notification tray never installed in the panel b/c I did not do a clean install/upgrade from 9.4..I downloaded it from the 'net? I'm still not sure why the automatic connection was lost all of a sudden. It worked flawlessly since April.

---

