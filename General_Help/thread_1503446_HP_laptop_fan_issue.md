---
title: "HP laptop fan issue"
date: 2010-06-06
forum: General Help
---

### Post by russianbandit on 2010-06-06
My laptop is HP dv4t-1000 and my fan (I'm guessing the cpu fan) is always on. This leads to short battery life and annoying noise of it running.
I do not see any reason for the fan to be on. My CPU temp stays under 50C most of the time. Is there any thing I can do to decrease the fan usage?

Here is an output of the only helpfull command I could think of:
```
cat /proc/acpi/fan/*/*
0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             49 C
critical (S5):           107 C
hot (S4):                105 C
passive:                 102 C: tc1=2 tc2=5 tsp=10 devices=CPU0 
active[0]:               68 C: devices= FAN 
```

---

### Post by lavinog on 2010-06-07
misread post

---

### Post by russianbandit on 2010-06-08
bump

---

### Post by lavinog on 2010-06-08
what video card do you have?
If it is an ATI card, are you using the fglrx driver?
The reason why I ask is because the open source driver has all of the power saving features disabled.  So even though the cpu isn't hot, the fan could be running because of the gpu is getting hot.

---

### Post by russianbandit on 2010-06-08
I've got an nvidia card and have the proprietary driver installed. nvidia-settings shows the card temp at around 60C.

---

### Post by lavinog on 2010-06-08
Can you post your dmesg?

---

### Post by russianbandit on 2010-06-08
I can post dmesg when I get home later today. Is there anything in particular I should look for?

---

