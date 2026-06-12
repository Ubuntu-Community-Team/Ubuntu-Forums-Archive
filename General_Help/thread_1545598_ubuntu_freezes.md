---
title: "ubuntu freezes"
date: 2010-08-04
forum: General Help
---

### Post by nos09 on 2010-08-04
well i have the problem using ubuntu 9.10 and 10.04 they both freezes after some time say like 2 or 3 min after login ..
even the live cd freezes too but sometimes it works (its strange )
and when i select the advance option form live cd = acpioff, it works fine form the live cd.
however my 9.04 ubuntu ultimate edition works fine. but i want to run 9.10 or 10.04
any guess whats the problem is or can anyone tell me how to turn off the acpi form command like in regular installation 

i have xp installed side by side (for my girl u know she dont use linux lol)

---

### Post by Rubi1200 on 2010-08-04
There may be a number of reasons why your system is experiencing these problems; software/hardware etc.
 
Posting your computer specifications such as RAM, hard-drive capacity, graphics card etc. would really help us get a better overview of your setup.
 
Also, take a look here and see if anything seems familiar:
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

---

### Post by StewartM on 2010-08-04
Do you have a graphics chip on the motherboard or a dedicated graphics card?

If the former, see: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

StewartM

---

### Post by nos09 on 2010-08-07
> sudo chmod a-x /usr/bin/compiz
n problem solved ..

---

