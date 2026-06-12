---
title: "Am I undervolting wrong?"
date: 2012-04-22
forum: General Help
---

### Post by MutantJohn on 2012-04-22
So I have an AMD Phenom II x4 955 BE processor and I tuned down the voltage through the BIOS of my MSI 870a-g54 MoBo.

I've heard undervolting is supposed to lower your temps and while under load, my cpu stays much cooler. As in, games that would make my CPU spike up to 59C (if not 60 to 61) now maybe peak 52C and remain consistently at 48C. 

So the undervolting is working while under load but my idle temps are higher than before I undervolted. Also, the BIOS doesn't like how low my voltage is and high recommends against it

Is there something wrong because undervolting is working but not working at the same time lol.

---

### Post by MonkeyPaw on 2012-04-22
Is Cool 'n Quiet disabled? Sometimes messing with factory settings leaves the CPU running at full speed, even at idle. This means it can't take advantage of the low power states that help save energy under low load.

Your board also has APS, which is an energy saving feature. You should have it enabled if it isn't already. Basically, it reduces power consumption depending on demand, which should typically result in lower CPU temperatures. If nothing else, it saves energy.

If CPU temps are still a concern, you might look into a better cooler. Many models will do a better job than the stock HSF, and run quieter too.

---

### Post by MutantJohn on 2012-04-22
Okay, so I found out what the issue was. Yesterday, I tried installing PHC or whatever and I think I kind of messed up some of my cpufreq settings.

So, when I'd type in cpufreq-info I'd get that I'm using the ondemand governor but the frequency range was set from 3.2 to 3.2 Ghz meaning all 4 cores were running at max stock frequency.

I have however changed all 4 since to scale from .8 Ghz to 3.2 Ghz and my CPU is cooler than normal actually. It doesn't rapidly spike like it used to and all seems well in my kingdom.

Thank you for your help anyway.

---

### Post by dcstar on 2012-04-23
> **MutantJohn said:**
> Okay, so I found out what the issue was.
........

Then **mark** the thread.

---

