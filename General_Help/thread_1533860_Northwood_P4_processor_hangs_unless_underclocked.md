---
title: "Northwood P4 processor hangs unless underclocked"
date: 2010-07-18
forum: General Help
---

### Post by J V on 2010-07-18
I'm running a machine with a 2.4 Ghz hyper threading processor: because 1.2 ghz sucks nowadays I'm going to turn hyper-threading off and give it a much needed speed bump.

Unfortunately, when setting the CPU to it's default 2400 Mhz (200 mhz bus speed) it hangs on boot and the bios gives a warning that the clock speed is incorrect.

This is wrong because in hyper threading mode at 1.2 Ghz per core it runs just fine - what is causing the hang? Bios firmware update?

---

### Post by RJARRRPCGP on 2010-07-18
You likely have bad caps: 

[http://badcaps.net](http://badcaps.net)

---

### Post by J V on 2010-07-18
So I just keep underclocking as little as possible to see how much I can get out of it? Any potential damage?

---

### Post by tgalati4 on 2010-07-18
Besides bad capacitors, quartz crystals age and slow down slightly.  So it's possible that the motherboard has a timing or interrupt problem.  Try cleaning out the machine, reseating all connections.  Reflashing the firmware on the motherboard.

Start at a slow clock speed and run for a few days.  Then increment to a higher speed and run for a few days.  Keep going until you get unstable operation.  If you find any bulging capacitors, either replace them or scrap the machine for something newer.

Replace the heat sink paste with something better (Artic Silver, etc).

---

### Post by J V on 2010-07-19
Well after a few more tests it seems to be running fine at 2400 single core now (Guess it just needed to be built up to it)

That shaved 14 seconds off my boot time lal :)

---

