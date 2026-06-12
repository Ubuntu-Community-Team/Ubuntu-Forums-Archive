---
title: "Ubuntu 11.04 Reboot Loop?!"
date: 2011-07-28
forum: General Help
---

### Post by Hatsune Miku on 2011-07-28
Greetings everyone, Another fun little bug ;-;. Did a nice clean install of Ubuntu 11.04 Minimal, installed NOTHING but the base system. Every time i try to boot the system off of the HDD, the kernel reaches to the point of assigning USB devices then reboots. I Tried removing ALL USB devices and got the same result. I have no clue AT ALL what could be going on.

The computer is rather old, but still usable for what I'm using it for.

Dell 3100
2 GB DDR2
P4 2.8 ghz HT (Prescott v2)
NVIDIA GeForce 5500 FX
WD Black 80GB 7200 RPM
320 Watt Power source.

All Assistance is LOVED and WANTED.

Thanks! Miku

---

### Post by 2F4U on 2011-07-28
An idea that may be worth trying is to boot off a liveCD and see if you can mount the partition Ubuntu is installed. If that works you can try to access the system log files. Maybe they contain a hint on why it is in a reboot loop.

---

### Post by Hatsune Miku on 2011-07-28
> **2F4U said:**
> An idea that may be worth trying is to boot off a liveCD and see if you can mount the partition Ubuntu is installed. If that works you can try to access the system log files. Maybe they contain a hint on why it is in a reboot loop.

Thanks for the tip! Did that and NOTHING is logged, NOTHING! /var/log has nothing of value :/

---

### Post by Hatsune Miku on 2011-07-28
FOUND THE PROBLEM!!! Its the stupid freaked nouveau; What ever jerk decides to make this is a real @#$#!!!! Anyway, how do i disable this on boot up?

EDIT: It might also be the libdrm file.... This sucks

---

