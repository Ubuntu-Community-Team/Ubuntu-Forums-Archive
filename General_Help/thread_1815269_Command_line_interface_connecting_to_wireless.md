---
title: "Command line interface connecting to wireless"
date: 2011-07-31
forum: General Help
---

### Post by Falc7 on 2011-07-31
I stupidly turned off my computer as I was updating to KDE 4.7. Now when i start it i get to the log in screen, but imputting my username and password just causes the Xserver to restart and i get back to the log in screen.

I know there are many other packages I should install as part of the update and i think this will solve my problem, so i am trying to connect to wireless through the command line login, and then install the updates.

I am having trouble connecting to the wireless though, here is what i am doing:

sudo iwconfig eth1 essid mercury_3D3CDE

sudo dhclient eth1

But it dosen't seem to work, those commands give me no output, what am i doing wrong?

---

### Post by nothingspecial on 2011-07-31
You sre using the ethernet interface eth1

try wlan0

to see your interfaces type ```
ifconfig
```

---

### Post by Falc7 on 2011-07-31
ifconfig lists 
eth0
eth1
lo

---

