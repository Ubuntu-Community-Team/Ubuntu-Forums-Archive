---
title: "Sound problem."
date: 2010-06-13
forum: General Help
---

### Post by Thatguyi445 on 2010-06-13
If I plug in headphones or speakers my laptop still plays the sound through the laptop speakers. I've been messing with the sound preferences, but nothing has helped. Help please.

---

### Post by jamesa00789 on 2010-06-13
I have a similar problem, the sound stops and nothing comes out of my headphones.

---

### Post by Thatguyi445 on 2010-06-13
Well I have sound coming out of both, I just don't want the sound to come out of my speakers when my headphones are plugged in.

---

### Post by Thatguyi445 on 2010-06-13
Bump?

---

### Post by lidex on 2010-06-13
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

