---
title: "nc6000 battery life"
date: 2009-10-05
forum: General Help
---

### Post by SuperGiraffe on 2009-10-05
Hi everybody,

My sister's laptop nc6000 has about 1 hour battery life in Ubuntu 9.04,  which is much shorter than when it had windows installed. i've used the powertop command to try and diagnose the problem but the suggestions it offers don't make a significant difference.
I've attached two powertop results to this post. I've installed powernowd to reduce the CPU speed and i've entered the command "iwconfig wlan0 txpower auto" to try and reduce the power consumption of the wireless card (DWL-G650).

Can anybody offer me some help? i would appreciate it.

Thanks,

---

### Post by zeroseven0183 on 2009-10-05
How long your sister has been using the laptop (with that battery)?

---

### Post by SuperGiraffe on 2009-10-06
I'm not sure. At least a couple years. We received the laptop second-hand from a friend.
It's a 10.8V 4.4AHr battery for use with [HP series PP2090, HSTNN-I01C family]("http://www.amazon.com/Hewlett-Packard-Battery-HSTNN-I01C-Presario-Business/dp/B001NHP2A2").It's Rev 2.02. with date code 950534.
Are you suggesting that the problem is the battery rather than Ubuntu? I only have ubuntu on the laptop now so i can no longer check if the battery life is better in windows but based on the battery specifications and the average consumption rate of 18W it should have around 2.5 hours of battery life.

---

### Post by Roasted on 2009-10-06
We have 600 laptops at work, and they're only 2 years old and one by one the batteries are having piss poor charge. Some laptops barely get a half hour of life.

There are many variables that could play a key role. Obviously the power settings in the operating system make for a huge factor, but on top of that, the big killer to batteries is leaving them plugged in all of the time. Does that laptop stay plugged into the AC adapter for long periods of time?

There's also a certain number of charges that laptop batteries tend to be rated for. For example, if you charge the ever loving hell out of that battery, chances are it will deplete at a much faster rate.

It's the unfortunate reality of rechargeable batteries. Although the OS plays a huge key role, and Ubuntu COULD be the issue, there's other factors to weigh in. 

For the record - My work laptop, which dual boots Jaunty and XP Pro, gets better battery power in Ubuntu than it does XP. Not by much, but enough to be noticeable.

---

