---
title: "&quot;dead&quot; area at the screen"
date: 2011-05-03
forum: General Help
---

### Post by SpinningAround on 2011-05-03
I have noticed something very strange with ubuntu, there is a small area in the center that is simply dead, it's displayed as it should but don't react to mouse clicks. It's almost like there was an invisible layer in front of everything, like a glass pane in Java, can't been seen but absorb mouse clicks.

---

### Post by aaron.fajun.chen on 2011-05-04
I can confirm the same problem.

Ubuntu 11.04 with unity
Mouse: Microsoft Comfort Mouse 4500
Thinkpad T60

---

### Post by aularon on 2011-05-05
I confirm that too, it's the same here. like a transparent rectangle to the middle bottom of the screen.

I tried the "Force Quit" applet, what happens when I click that area is the "Force Quit" prompt disappears (so it got the click), but it doesn't show the confirm quit prompt (as what happens when clicking anything else), nor it removes that area.

---

### Post by iceman on 2011-05-25
Same thing here!
My dead area starting at 490x350 (up/left)... is 50 pixels height and it's 750pixel length! (i have 1366x768 resolution)
I can restore everything by start "compiz --replace" but i don't know how i am "triggering" the event which "dead area"...

Please, let me know if you solve the problem

---

### Post by Psychobudgie on 2011-05-25
> **iceman said:**
> Same thing here!
My dead area starting at 490x350 (up/left)... is 50 pixels height and it's 750pixel length! (i have 1366x768 resolution)
I can restore everything by start "compiz --replace" but i don't know how i am "triggering" the event which "dead area"...

Please, let me know if you solve the problem

Exactly the same issue here. Glad to see I'm not going mad.

---

### Post by iceman on 2011-05-25
I tried this repository:
sudo add-apt-repository ppa:xorg-edgers
sudo apt-get update
sudo apt-get dist-upgrade

Now i don't have the problem... but i experienced two xorg crash in a couple of hour... and i can't rollback anymore! I don't want to reinstall... i started upgrading my system from 7.04!! (7.10->8.04->8.10->9.04->9.10->10.04->10.10 and now 11.04)

---

### Post by iceman on 2011-05-25
Nothing... problem persists!
I think i will reinstall from scratch :(

---

### Post by iceman on 2011-05-25
Amazing! I discovered why this happens!!
ALT-TAB "triggers" the dead-area!!
The solution is to disable Static Application Switcher and to set Shift Switcher as "default" (changing Super+TAB to ALT+TAB) thru CCSM.
The most important thing is to logout/login again after changes (because they will not function on active session)

---

### Post by SpinningAround on 2011-05-27
> **iceman said:**
> Amazing! I discovered why this happens!!
ALT-TAB "triggers" the dead-area!!
The solution is to disable Static Application Switcher and to set Shift Switcher as "default" (changing Super+TAB to ALT+TAB) thru CCSM.
The most important thing is to logout/login again after changes (because they will not function on active session)

Sounds good but where do I change it?

---

### Post by iceman on 2011-05-27
I wrote it... CCSM! Google it... First link...

---

