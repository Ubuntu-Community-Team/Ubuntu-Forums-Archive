---
title: "power consumption monitor software"
date: 2009-06-26
forum: General Help
---

### Post by bwitherell on 2009-06-26
Hello,

I was hoping that someone could suggest a some decent power consumption monitoring software to run on desktop hardware.

I tried to a few packages but they seemed to be more tuned for laptops and would give me measurements in Watt/hours. Pwrkap also does not work for my hardware.

Basically I need some software that will tell me how many Watt/hours or kilowatt/hours my system (an old P3 Gateway tower) is using. Is there anything out there that might do what I need? :confused:

Any help would be very appreciated. Thank you.

---

### Post by sdennie on 2009-06-26
The way these tools work (or at least the way powertop works) is they essentially infer the information by looking at battery charge differences over a fixed amount of time.  Though, sometimes the battery itself simply reports this information via the BIOS.  If you don't have a battery I'm not sure if any piece of software has enough information to tell you how much power you are using.  I think you'd have to use a multimeter or some kind of hardware to get these numbers.

---

### Post by bwitherell on 2009-06-26
ahhh, Just what i feared the problem was. I was hoping that would not be the case. Anyway, thank you very much for the quick response.

---

### Post by mcduck on 2009-06-26
> **bwitherell said:**
> ahhh, Just what i feared the problem was. I was hoping that would not be the case. Anyway, thank you very much for the quick response.

At least in here you can usually borrow a small wattmeter and/or electricity meter for free from your electricity company. Of course that might not be the case there, but you could always ask them?

(the only way to meter the real power usage of a computer is to measure the electricity drawn by the power source, no software or hardware inside the computer itself can give you accurate results as the PSU itself isn't 100% efficient and will thus always draw more power than it feeds into the computer.)

---

