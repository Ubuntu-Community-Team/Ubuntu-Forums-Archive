---
title: "Game crashes"
date: 2009-08-24
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-08-24
Recently Nexuiz has started crashing on me for some reason. I get "segmentation fault" In the terminal and thats it. If some1 could let me know what that means, that would be great, and/or what could be causeing this. thanx.

---

### Post by Ms_Angel_D on 2009-08-24
Sorry I can't help with your issue but you might want to try the Nexuiz Forums Found Here: [http://alientrap.org/forum/index.php?c=3](http://alientrap.org/forum/index.php?c=3) Good Luck!

---

### Post by automaton26 on 2009-08-24
If Nexuiz has been working for some time, and you haven't installed or changed anything recently, you might try checking your memory for faults.

To do this you can run *memtest* from the boot menu (ESC), or from a Live CD.

If that's OK, you might try checking your hard disk too.

---

### Post by Feelin_froggy8877 on 2009-08-24
Thanx for the reply's. Wasn't sure where to start, as far as what could be wrong. I don't actually have it installed on ubuntu. I run it from a term from its folder location on a hdd that is used strictly for storage of personal files. And since you had mentioned possibly checking my disk, I'll try installing the .deb package and see what happens.

---

### Post by Feelin_froggy8877 on 2009-08-25
O.k, I installed nex in ubuntu and everything seems good (no crashes) But....I decided to run the memtest anyway for #@$% and giggles and for some reason I'm getting a thermal event about 10 sec in every time. I have never had a thermal event till now (running memtest). Does the memtest put excessive stress on the cpu?

---

### Post by P4man on 2009-08-25
Is that "thermal event" a message in memtest ? I didnt even realize it tested temperatures? Does it say anything more, does it relate to the cpu, or possibly the motherboard?

Normally, running memtest wouldn't be all that stressful for the cpu. It does stress the RAM modules very much, and therefore also the memory controller. If you have AMD Atlon 64 or newer, or a very new intel Core i7, the memory controller is part of the cpu.

Anyway.. im not too sure what it means, but it could be your cpu is throtteling. That is, doing iddle cycles to prevent it from overheating. Wouldnt hurt checking your temps in the bios, and if needed, take measures (new cooler, reapply thermal grease, clear heatsink, ...)

---

### Post by Feelin_froggy8877 on 2009-08-25
Sorry, should have been more specific. Not a read out in the memtest, computer shuts down after about 10 sec into the memtest. Get the thermal event message after reboot. Cpu is a Pentium 4, 2.40 ghz, 1.5 gb ram on a OptiPlex GX270 dell mobo. And the bios seem a bit limited on what I can do. No temp or clock speed info. Been trying to find a decent app for this, but not having much luck. And I guess It would be possible to flash/update bios but not sure how to go about that.

---

### Post by Feelin_froggy8877 on 2009-08-25
I realize this got way off the original question so I started a new thread. Thanx for the help people.

---

### Post by P4man on 2009-08-26
I dont think it went very much off topic. What causes your pc to shut down in memtest is probably what caused those segmentation faults too.

Are you sure its an overheating problem? Open the case and check if the fans are running (also of your videocard!) and if the heatsink of the cpu is too hot to touch or not. It can also be your powersupply is failing.

---

### Post by Feelin_froggy8877 on 2009-08-26
Well I'm not completely sure it is overheating, Just figured thats what it was. "last shutdown was due to a thermal event, press f1 to continue or f2 to enter setup" And wasnt sure why running the memtest would cause that.

---

### Post by P4man on 2009-08-26
> **Feelin_froggy8877 said:**
> Well I'm not completely sure it is overheating, Just figured thats what it was. "last shutdown was due to a thermal event, press f1 to continue or f2 to enter setup" And wasnt sure why running the memtest would cause that.

well thats a pretty clear error message. Good points for the BIOS :)
Check your CPU heatsink/fan. If you are not comfortable messing around with PC hardware, ask a friend or go to a shop. Either your fan broke, or the heatsink isn't mounted properly.  Check the BIOS also if it has a setting at what temp it shuts down.. possibly (though not likely) its ridiculously low.

---

### Post by Feelin_froggy8877 on 2009-08-26
Well, I'm the 1 that built the comp, And I should have known it was the heatsync. When I was putting it together, the mount for the heatsync wasn't quite right. I did think I had gottin it seated pretty good, but I guess not. An dwhen I got the thermal message, it through me off, thinking it had nothing to do with the processor, since I was testing the RAM. Guess I got some work to do (haha) And I cant get no sensors to work, all I can get a readout from is a hhd, and even that don't seem right. In the sensors applet preferences the only sensor  available is hddtemp (/dev/sg1 Maxtor & /dev/sdb Maxtor), now I only have on maxtor hdd with 2 partitions and 3 hdd's in my comp.

---

