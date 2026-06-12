---
title: "Fan control."
date: 2009-11-19
forum: General Help
---

### Post by emshains on 2009-11-19
I recently added an additional intake fan, because there was no air for other fans to push out of the box, and now I get around 5 *C off of load temperatures. The problem is, it is as loud as my vacuum cleaner, and that may be a little too loud. Is there a way to control case fans ? I've come across only cpu fan control, which in my case is done by BIOS.

I'm running an am2 sli motherboard from asus, I assume the chipset is n670 or something like that, I hope this helps.

---

### Post by prem1er on 2009-11-19
Does the fan connect to the mother board, or is it only plugged into the power supply. If the latter, than you cannot control the fan.

---

### Post by emshains on 2009-11-19
I tried both, and even though I set the fans to be silent ( in the bios), it still sounds like a vacuum cleaner.

---

### Post by whitethorn on 2009-11-19
Have a look at lm sensors.  I think it's called lm_sensors, there's a package that comes along with it called fan control.  Just make sure your fan is connected to the motherboard.  

Here's a Howto for Fan Control
[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

Just look for another howto about how to set up lm_sensors.

---

### Post by jimpr13 on 2009-11-19
I consider that if you haven't connect motherboard there isn't any other solution

---

### Post by emshains on 2009-11-19
Oh well. I will canibalize a seperate fan controller from another PC, since it didn't fix the problem in that PC. In fact, I took the same fan that's causing problems here from that pc. The thing is though, when I had connected it to an older PC, it ran just fine without any problems for over a year.

EDIT: I tried to run that old P4 without the separate fan controller, but then that was turned into a vacuum cleaner.

---

