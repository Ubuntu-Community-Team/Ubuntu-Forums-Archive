---
title: "PPPoE Connection problem"
date: 2011-05-21
forum: General Help
---

### Post by steryman on 2011-05-21
*sorry if posted in wrong section*
Hi guys today I installed Ubuntu 11.04 and configured the PPPoE connection (I'm using PPPoE broadband) correctly, I click on it to connect, the circle is moving in the icon tray for about 5 seconds and then it says disconnected. I am sure that I configured it well because in Windows XP is working :) Please help me fix it!

P.S.: I am not new in ubuntu, I used this PPPoE connection in earlier versions and worked fine.

---

### Post by gandaran on 2011-05-21
> **steryman said:**
> *sorry if posted in wrong section*
Hi guys today I installed Ubuntu 11.04 and configured the PPPoE connection (I'm using PPPoE broadband) correctly, I click on it to connect, the circle is moving in the icon tray for about 5 seconds and then it says disconnected. I am sure that I configured it well because in Windows XP is working :) Please help me fix it!

P.S.: I am not new in ubuntu, I used this PPPoE connection in earlier versions and worked fine.
which did you use for the setup? network manger or pppoeconf?
if you did not use pppoeconf try it.
```
sudo pppoeconf
```

---

### Post by steryman on 2011-05-21
Ok thanks it works now :) But it's a bit laggy... is it because of the new firefox right? Because on Windows XP on Firefox 4 it moves laggy... I use Opera. Anyway, Thank you again!

One more question, the new connection is called ppp0 right? So if I want to bridge it with another one I must use this name? I want to bridge it with USB tethering connection from Xperia Arc to reverse tethering to get internet on the phone :)

---

### Post by gandaran on 2011-05-22
> Ok thanks it works now  But it's a bit laggy... is it because of the new firefox right? Because on Windows XP on Firefox 4 it moves laggy... I use Opera. Anyway, Thank you again!
try the Chromium browser (not Google Chrome) from the software package manager, Chromium beats any other browser including Chrome on speed.

---

