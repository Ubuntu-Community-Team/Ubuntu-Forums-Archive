---
title: "excessive heating?"
date: 2011-04-30
forum: General Help
---

### Post by awambawamb on 2011-04-30
Hi guys
this time I'm asking you advice about excessive heating of a part of my laptop, a zd8369ea.
All the three fans under the laptop work - whe i was in WinBlows environment, only 2 of them worked. :D
the problem however is an excessive heating of a un-fanned part just over the battery. I'm attaching two picture of the hot zone took from a spare motherboard i had at home, maybe someone with technical skills could understand why this part is getting hot when using ubuntu. the first one is where the heat is located, the second one is the zoom on the hot part.
the heat level is "hot", i haven't measured it but it's way hotter than before.
thanks a lot
Max

---

### Post by KegHead on 2011-04-30
Hi!

Check to see if you can update your bios.

Also;

update your kernel;

sudo apt-get update

sudo apt-get install linux-image -f

Restart.

KegHead

---

### Post by awambawamb on 2011-05-02
> **KegHead said:**
> Hi!

Check to see if you can update your bios.

Also;

update your kernel;

sudo apt-get update

sudo apt-get install linux-image -f

Restart.

KegHead


didn't really helped. bios is the last one available. anyone know what part of the mainboard is the circled one? it could help future users from hp with other Qanta motherboards maybe.

---

### Post by awambawamb on 2011-05-03
anyone here can figure asolution for this? why does my motherboard il heating so much?
it IS a software issue,as under windows i had no overheating at all
:(

---

### Post by awambawamb on 2011-05-03
googling (and pulling my long hair out of my head) around i noticed that there are 2 R56W-4C5654J inductors in the area of the heating. could they be the source of my problem? Inductors are said to tranform electrical energy to heat. looking forward to the solution - using ubuntu.

---

### Post by awambawamb on 2011-05-03
I got the name of the overheating components. PL8 and PL14. What are those components used for?

---

### Post by notoriousdbp on 2011-05-03
Are you using ATI graphics by any chance?  The open driver is known for generating a lot of heat.

---

### Post by ivanovnegro on 2011-05-03
Also, are you using Ubuntu 11.04, its a known issue that the newest Kernel 2.6.38 on Natty has a power regression (with some hardware), also it produces more heat, energy.

---

