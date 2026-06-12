---
title: "What are normal sensor readings"
date: 2010-04-30
forum: General Help
---

### Post by Inder on 2010-04-30
Hi there,

I've been having trouble with my laptop suddenly shutting down sometimes. I think it may be overheating, so I just wanted to check with you guys if my temperature is higher than normal. When I start the computer and run sensors, here is what I get:
> 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +82.0°C  (crit = +99.0°C)                  
temp2:       +75.0°C  (crit = +126.0°C)

Are these temperatures normal considering I just started the computer up? It just seems high because I have only 17°C to go before reaching a critical temperature... What if I start playing a game or do 3d modeling? 
So yeah, is this normal?

Thanks,

Shawn


btw, I just run the sensors command for a second time after writing this thread and now it reads:
> 
acpitz-virtual-0
Adapter: Virtual device
temp1:       +73.0°C  (crit = +99.0°C)                  
temp2:       +66.0°C  (crit = +126.0°C)


---

### Post by jobix on 2010-04-30
They seem very high. On my four year old desktop (AMD64 X2) with a bunch of applications running including Firefox open with 40+ tabs, I get about 45 C. 82C seems very high especially for a laptop.

---

### Post by Inder on 2010-04-30
****, that's not at all what I wanted to hear. So what do I do now? Is there an easy way to find out why it's overheating?

I guess I should give you my specs..
> Acer Aspire 5536-5519
AMD Athlon 64X2 processor
QL 64(2.1 GHz)
ATI Radeon HD 3200 Graphics
Up to 1919 MB HyperMemory
15.6" HD LED LCD
4GB Memory
320 GB HDD
DVD Super Multi DL drive

running Ubuntu 9.10 Karmic Koala

---

### Post by The Real Dave on 2010-04-30
Your laptop is quite powerful, but those temps are a bit on the hot side. 

Dust and dirt in your laptop can cause high temps. Get a can of compressed air, and clean out it's insides, if you feel comfortable opening it up. You'd be amazed at the gunk you'll find in there. I recently cleaned my sister's laptop and found an inch thick of solid dust between the blower and the heat sink. Before cleaning it had been running extremely hot, now, the temps are much lower.

Also, you could buy or make a laptop stand with cooling fans, to help cool that thing down.

EDIT: My 3Ghz Pentium IV [Desktop] computer with a little tinkering runs full tilt at 35C, and idles at 28C, when clean that is. Not bad, bearing in mind that Pentium IVs are generally a hot chip :) </brag>

---

### Post by jobix on 2010-04-30
I'd follow The Read Dave's suggestions above. If you don't feel like opening it up, you can try to use a vacuum cleaner and suck up all the dirt.

Another thing that occurred to me is that on my laptop, if I don't keep it on a flat surface, I do notice it getting a bit warmer than usual. Nowhere near 82C though. Turns out there are some small knob like things under the laptop which keep the entire bottom surface about half an inch above the table, i.e., there is no direct contact. This helps in heat dissipation. So, if I put it on a soft surface like a bed/sofa, this gap is no longer there and therefore there is no heat dissipation via that route. I don't know if this applies to your situation.

---

### Post by The Real Dave on 2010-04-30
> **jobix said:**
> I'd follow The Read Dave's suggestions above. If you don't feel like opening it up, you can try to use a vacuum cleaner and suck up all the dirt.

Another thing that occurred to me is that on my laptop, if I don't keep it on a flat surface, I do notice it getting a bit warmer than usual. Nowhere near 82C though. Turns out there are some small knob like things under the laptop which keep the entire bottom surface about half an inch above the table, i.e., there is no direct contact. This helps in heat dissipation. So, if I put it on a soft surface like a bed/sofa, this gap is no longer there and therefore there is no heat dissipation via that route. I don't know if this applies to your situation.

It applies to almost all laptops. Those little legs let air flow under the laptop, and let it pull air to cool itself. Imagine trying to breath through your bed ;) Same principle

---

### Post by Inder on 2010-05-01
I just took the crap out of between the keys and shot some compressed dust-removing gas in pretty much every opening. This is what sensors look like now:
temp1:       +68.0°C  (crit = +99.0°C)                  
temp2:       +61.0°C  (crit = +126.0°C)

And on startup it's even a bit lower ( > 53 )

It's still a bit hot don't you think?
Do any of you have good tutorials on how to safely open the bugger up and clean it from the inside?

Thanks a lot for the help so far!

Shawn

---

### Post by jobix on 2010-05-02
I don't have any tutorials on hand, but I've done it before. It's quite easy. You can try doing a web search or even a search on Youtube for how to open up a laptop.

Just something to keep in mind: using compressed air to blow stuff is not bereft of danger if you have it closed - you could end up pushing dirt further inside. Think of it like trying to use a Q-Tip in your ears - you could end up pushing the stuff further inside the ear. ;-) So, it's better to have the laptop open before you start blowing air. That's also why I recommended using a vacuum instead since that way you are not blowing into the laptop and instead sucking the stuff outside. Anyway, seems to have worked for you. 68C is not too bad, not the best, but not too bad either. Good luck.

---

