---
title: "Network manager and volume control icons missing"
date: 2010-02-24
forum: General Help
---

### Post by anur.bhargav on 2010-02-24
Hi everybody,
The Volume control and network manager icons are not visible in the notification area..
I sure its has nothing to do with 
Add to panel-->Notification area....beacuse the notification area is already there..
but the icons are not visible
the only way that I can make the visible is by typing
> Alt+F2 and running the commands > nm-applet --sm-disable for Network Manager and > gnome-volume-control-applet for volume control.. Only then they become visible in the notification area

Both, the network manager and volume control are mentioned in the "Start-up programs",yet I have this problem
Please HELP!!:(

---

### Post by mikewhatever on 2010-02-24
Right click on the panel and add the Notification Area, that's where both the Volume and the NM live.

---

### Post by drdanielfc on 2010-02-24
> **anur.bhargav said:**
> Hi everybody,
The Volume control and network manager icons are not visible in the notification area..
I sure its has nothing to do with 
Add to panel-->Notification area....beacuse the notification area is already there..
but the icons are not visible
the only way that I can make the visible is by typing
 and running the commands  for Network Manager and  for volume control.. Only then they become visible in the notification area

Both, the network manager and volume control are mentioned in the "Start-up programs",yet I have this problem
Please HELP!!:(

Have you added those two commands to your list?
Also, try putting a 'Z' in front of them so they load last (workaroundy but its solved some problems for me)

Also, try a script that sleeps for 10 seconds before it loads those things up

---

### Post by anur.bhargav on 2010-02-25
> **drdanielfc said:**
> Have you added those two commands to your list?
Also, try putting a 'Z' in front of them so they load last (workaroundy but its solved some problems for me)

Also, try a script that sleeps for 10 seconds before it loads those things up
I put a 'Z' in front but that din't help..

---

### Post by drdanielfc on 2010-02-25
> **anur.bhargav said:**
> I put a 'Z' in front but that din't help..

a script that sleeps for 10 secs then loads them?

---

### Post by anur.bhargav on 2010-02-26
> **drdanielfc said:**
> a script that sleeps for 10 secs then loads them?
I dont know how to do that..Please teach me how to do it

---

### Post by drdanielfc on 2010-02-26
> **anur.bhargav said:**
> I dont know how to do that..Please teach me how to do it

Open up gedit and paste this in:
```
#/bin/bash
sleep 10
nm-applet --sm-disable
gnome-volume-control-applet
```

save it in your home folder as *loadvol.sh*

Add a command to your sessions that uses:
```
sh /home/YOURUSERNAME/loadvol.sh
```

---

### Post by anur.bhargav on 2010-02-26
> **drdanielfc said:**
> Open up gedit and paste this in:
```
#/bin/bash
sleep 10
nm-applet --sm-disable
gnome-volume-control-applet
```

save it in your home folder as *loadvol.sh*

Add a command to your sessions that uses:
```
sh /home/YOURUSERNAME/loadvol.sh
```
Thanks ... but i got the icons back... the problem was, i was logging in "failsafe Gnome" mode..once i changed that i got back the icons:popcorn::p
Anyways thanks for the support

---

