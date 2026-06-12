---
title: "High Pitched Sound when I turn my computer on"
date: 2009-09-29
forum: General Help
---

### Post by SonOfWolf on 2009-09-29
When I installed Ubutntu 9.04, when ever I turn my computer on it makes a high pitched beep for the internal speaker. It never used to do that?

Is there anyway to stop the system doing that high pitch beep?

The system works fine apart from that so unsure as to what the beep is all about its just annoying and startles friends when they use my machine :lolflag:

---

### Post by ApEkV2 on 2009-09-29
How old and what model computer are you using?

---

### Post by tom66 on 2009-09-29
Press F2 or Del or Ins (try all of them) to enter the system setup, then look for an option to turn off the system beep. Then try to find the save changes and exit option. Unfortunately all BIOSes are different so these are generic instructions - you'll have to figure it out yourself.

---

### Post by SonOfWolf on 2009-09-30
My computer is self built.
Motherboard is P5Q Deluxe. 4GB RAM. GTX 260. Intel Quad Q6600. 

This beep only happened after installing Ubuntu. Weird huh?

---

### Post by tom66 on 2009-09-30
It's possible Ubuntu wrote to the RTC function of the BIOS to enable some features.

---

### Post by mcduck on 2009-09-30
> **tom66 said:**
> It's possible Ubuntu wrote to the RTC function of the BIOS to enable some features.

Actually that sounds very, very unlikely. :D

Anyway, are you sure the sound is actually comping from the beeper? it it's *very* high pitch then it's more likely coming from your motherboards power regulatory components (annoying phenomenon known as "coil whine"). They can cause a very-high-pitched sound depending on the load they are running, and Linux might be causing a slightly different load on your system than Windows does. In that case any electrician will be able to spray some electronics lacquer to the components to stop the sound.

If it's a desktop machine, open the case and try to listen where the sound is coming from.

Of course if the sound *is* coming from the beeper, you just need to open your motherboard's manual t check what error code the beep is related to.

---

