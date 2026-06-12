---
title: "'out of range' problem, monitor"
date: 2010-03-06
forum: General Help
---

### Post by Crypz on 2010-03-06
so i tried to install linux mint, at first i got 'out of range' with black screen msg but used compability mode and got past it and installed mint on my HD. 

a moment after it updated my nvidia drivers and after reboot I got the out of range message again, which leaves me in the situation where i cant do pretty much anything 

I tried editing xorg.conf
added 

VertRefresh 60-75
and
Modes "1440x900_75.00"

but that didnt get it fixed, help help

---

### Post by Intrepid Ibex on 2010-03-06
So are you certain your screen is capable of those settings?

---

### Post by Crypz on 2010-03-06
I have 1440x900 n 75 hz on my windows right now.

also, i went to the recovery mode to the command line and tried out typing startx. got in from there, opened nvidia-settings, did 1440x900 and 75 hz, saved that to the xorg.conf settings, rebooted, still "out of range"

---

### Post by Crypz on 2010-03-06
needs halp

---

### Post by Easy Limits on 2010-03-06
Try knocking your Hz down to 60 if you are using an LCD monitor.

---

