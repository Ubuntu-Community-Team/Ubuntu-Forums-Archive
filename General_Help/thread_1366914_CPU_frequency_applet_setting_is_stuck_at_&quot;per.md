---
title: "CPU frequency applet setting is stuck at &quot;performance&quot;?"
date: 2009-12-28
forum: General Help
---

### Post by mahela007 on 2009-12-28
I have an IBM laptop with celeron M at 1.5 GHz. Since ubuntu doesn't support frequency scaling on this CPU by default, I had to add the necessary module to the kernel. (Called p4clockmod.. or something like that). Now, the system does appear to be able to scale automatically but it  very rarely sends the CPU frequency below it's maximum.. I tried changing the settings in the frequency applet to options like "powersave" and "ondemand". Those options don't seem to work. Every time I check back, the "performance" option has been reselected.
????

(Also, whenever the frequency is scaled down , it takes too long to respond to increased processing requirements. In other words, it takes about half to one second to increase the clock speed when do something like I drag a window )

---

### Post by FactTech on 2011-03-10
You can find specific details about the cause of this issue at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432706)

It isn't fixed in Lucid yet as of today, though.

---

