---
title: "Dual monitors, mice, and keyboards."
date: 2009-12-15
forum: General Help
---

### Post by sparky8251 on 2009-12-15
I'm sure this has been asked before but I'll ask it anyway. If I have a computer that has two monitors set up and has two mice and key boards plugged in, is there any way that I can have two users log in to the same computer using different monitors, mice, and keyboards?
That is, can I have two users doing two different tasks on separate monitors.

---

### Post by sparky8251 on 2009-12-16
bump

---

### Post by Portmanteaufu on 2009-12-17
I believe you're looking for "MultiseatX" -- perhaps [this link]("https://help.ubuntu.com/community/MultiseatX") will address your needs?

---

### Post by sparky8251 on 2009-12-18
"MultiseatX" is what I am looking for but there is no description of how to set it up on karmic. If anyone could provide such information it would be nice.

---

### Post by llawwehttam on 2009-12-18
Setting up a multi-seat machine "manually" does not work any more because gdm 2.28 does not use /etc/gdm/gdm.conf-custom . If you switch to gdm 2.20 all will work like with 9.04

So to put it briefly you have to downgrade gdm to 2.20 and then follow the instructions for jaunty

---

### Post by sparky8251 on 2009-12-18
So there is no way to set it up using gdm 2.28? If not how would I downgrade?

---

### Post by sparky8251 on 2009-12-23
bump

---

