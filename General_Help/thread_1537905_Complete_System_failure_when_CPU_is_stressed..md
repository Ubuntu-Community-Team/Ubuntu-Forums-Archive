---
title: "Complete System failure when CPU is stressed."
date: 2010-07-24
forum: General Help
---

### Post by charliehorse55 on 2010-07-24
I get a complete system failure when my CPU is stressed. It's not the temperature because when it crashes the CPU temp is only ~55 C.

When it crashes the video freezes but the sound repeats itself. Example. I start handbraking a movie, then open a tv show in VLC. This is what I hear. 

Hello.
Hey. 
Did you get that tire - then it freezes
get that tire
get that tire
get that tire
get that tire
... etc

That continues until I reboot my computer. This crash is pretty reliable, as every time I load my CPU that happens. 

If I don't do anything CPU intensive, I don't get the crash. Also, if I only load up one core of my CPU, then everything is fine. However if I run something such as prime95 or handbrake (which both utilize all 4 of my cores) the computer will crash within 30 seconds. 

Help?

Ubuntu 10.04

Corsair 750 TX PSU
AMD Phenom x4 @ 2.3 GHz
4 GB G.Skill 1066 DDR2 Memory
Nvidia GTS 250 1 GB edition
Biostar AMD 770 AM2+/AM2 Motherboard

Three HDs, two are WD of 1 TB and 120 GB, and a 32 GB SSD.

---

### Post by prodigy_ on 2010-07-24
> **charliehorse55 said:**
> @ 2.3 GHz
Overclocked?

---

### Post by charliehorse55 on 2010-07-24
> **prodigy_ said:**
> Overclocked?

No, stock. 1.25 V as well. 

It's a AMD 9600 Phenom x4 Black Edition (BE means unlocked multiplier, but this chip doesn't really OC)

---

### Post by prodigy_ on 2010-07-24
Still looks like a possible hardware issue to me. Not necessarily CPU-related though. Faulty RAM maybe?

---

### Post by kaldor on 2010-07-24
Try removing the RAM to see if it was loose or damaged. I've seen a laptop with problems kinda like what you're having, and the RAM wasn't fully seated.

Did this problem always occur on Ubuntu 10.04? Did it happen on your previous OS or distro/release?

---

### Post by charliehorse55 on 2010-07-24
The problem for me is that, I haven't put much stress on my computer at all reccently. I think the last time I did anything super cpu intensive was in feburary :D. 

I did just put a new motherboard in, but I had the problem before the new motherboard. (My old mobo was fried by lightning.)

I replaced the mobo and then everything seemed to work fine. 

I have an extra HD, I'll reboot install windows on it and see if it can handle prime95 for more than 5 min.

---

### Post by charliehorse55 on 2010-07-24
I feel so stupid now. My new motherboard that I bought, it is crap. (I only plan on using it until december)

It only supports 95W CPU. I have a 125W CPU. So when the benchmark starts, the CPU goes over wattage. 

The reason that it doesn't happen the second that I start the benchmark is becase CPUs use more power the hotter they are. So I must be using like 94W, then the CPU heats up and the power usage goes over 95W. 

Fixed it by underclocking my chip from 2.3 GHz to 2.0 GHz and reducing volts to 1.20

---

