---
title: "Inconsistent Boot Times"
date: 2012-01-15
forum: General Help
---

### Post by nmaster on 2012-01-15
I installed ubuntu from the 64-bit minimal cd (I didn't want a desktop environment but instead have a custom Openbox setup). 

I've noticed big differences in the boot times reported by bootchart but I'm having trouble interpreting the charts. I've attached bootcharts from a "fast" boot and from a "slow" boot. The fast boot takes 43 seconds and the slow boot takes 67 seconds. The "slow" boot is more typical and usually boots take more than a minute.

One difference I notice is that on the slow boot, I see a switch off between flock and laptop_mode, but I'm not if that is a problem, a symptom of a problem, or no problem at all.  

Does anyone have any suggestions?

---

### Post by nmaster on 2012-01-19
does anyone else have similar problems?

---

### Post by nmaster on 2012-01-26
bump

---

### Post by raja.genupula on 2012-01-26
> **nmaster said:**
> I installed ubuntu from the 64-bit minimal cd (I didn't want a desktop environment but instead have a custom Openbox setup). 

I've noticed big differences in the boot times reported by bootchart but I'm having trouble interpreting the charts. I've attached bootcharts from a "fast" boot and from a "slow" boot. The fast boot takes 43 seconds and the slow boot takes 67 seconds. The "slow" boot is more typical and usually boots take more than a minute.

One difference I notice is that on the slow boot, I see a switch off between flock and laptop_mode, but I'm not if that is a problem, a symptom of a problem, or no problem at all.  

Does anyone have any suggestions?

1st thing i am unable to see that image .

I think some modules which are not having high priority they may be skipped in fast booting mode .

In slow booting mode i think irrespective of priority all are executing . 

So that's make the difference , this is what i am thinking .

---

