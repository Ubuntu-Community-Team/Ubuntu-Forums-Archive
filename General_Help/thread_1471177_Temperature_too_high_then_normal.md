---
title: "Temperature too high then normal"
date: 2010-05-03
forum: General Help
---

### Post by genozzolo on 2010-05-03
Hi

Ive the current problem.

If I install Linux Mint 8 or Open Suse , temperature is 48 as windows mostly.


If I install any other distro, temperature goes to 80-85 and fan is always On.

Ive a laptop dell just bought it, dell studio 15, 4ghz ram dual core etc, a monster for linux but ive this problem, kinda annoying when you wanna have something silent and that doesnt become a furnace.


Any clue ?

No process that use cpu while Idle.

I installed Lm-sensors, ive to do something with it ?

---

### Post by genozzolo on 2010-05-03
this happens with ubuntu 9,1 and also lubuntu 10.4 and so on.

not just 1 distro but many.

---

### Post by gionata on 2010-05-06
I'm experiencing the same problem, since I upgraded to 10.4.

but I do not rely experience temperature as 9.10 (< 50° idle)

my sensors give out in idle a kind of

$ sensors|grep Core
Core 0:      +73.0°C  (high = +86.0°C, crit = +100.0°C)  
Core 1:      +70.0°C  (high = +86.0°C, crit = +100.0°C)  

with normal activity temperature give ALARM

In some forum I found that this would be a problem related to GFX
suggesting to install proprietary driver for my
VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD  4350]

but still too high temperature.

Is there anybody that do not have this problem?

---

