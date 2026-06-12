---
title: "Hardware diagnostics"
date: 2011-08-24
forum: General Help
---

### Post by kerryhall on 2011-08-24
So someone spilled beer on my motherboard. (Me) Everything seems to be working fine, but I was wondering if there are any hardware diagnostic tools that can be used to verify that everything is working properly on my motherboard. I would like to test RAID controllers, buses, sound card, ata controllers, video capture card in pci slot, etc. Basically every chip on there. Is that possible? I am already familiar with RAM and hard drive diagnostics.

---

### Post by kerryhall on 2011-09-21
Bump

---

### Post by ingramproductions on 2011-09-22
Bump

---

### Post by Linuxisfast on 2011-09-22
You need hardware tester, cant be done via software, OTOH, if your system is booting, then all is well.

---

### Post by coldraven on 2011-09-22
I once had to fix a high speed printer that someone (not me!) had spilled coffee into.
The sugar in the coffee had actually eaten through one leg of a capacitor.
Well I am not a chemist but I presume it was the sugar.
I washed the mother board with warm water (not joking) and replaced the capacitor.
It worked fine afterwards. How sweet was that beer?

P.S. If you did try that I would leave the board in a warm place for at least a week before you power it up.

---

### Post by kerryhall on 2011-09-22
The system was actually running at the time and nothing bad happened. It's been working fine since then. My question is less about my particular situation and more about testing hardware in general. For example, if I purchase a used motherboard, it would be nice to know if anything is wrong with it. I realize that trying to test hardware using software running on that hardware might seem counterintuitive, but if the processor and ram work fine, it seems like it should be possible to test the other subsystems on the motherboard. For example, raid controllers, integrated sound, integrated video, etc. Or, what about testing pci cards such as a video capture card or a pci raid controller? 

Thanks!

---

### Post by patryk77 on 2011-09-23
I am pretty sure that would have to be done on the hardware (chipset) level and on the driver level, which would be pretty much unthinkable with the amount of hardware / drivers available.

It would be a nice idea, but it doesn't sound feasible until all the hardware vendors agree on a standard, or someone (way smarter than me) comes up with such a standard with an open source license that is open enough (BSD?) that hardware vendors would be able to include it in their hardware royalty-free and without too many restrictions.

Unrelated note: sending you a friend request because any *nix user with Bakunin in their sig is a friend of mine :guitar:

---

