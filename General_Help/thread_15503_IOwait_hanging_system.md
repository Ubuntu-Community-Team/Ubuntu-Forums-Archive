---
title: "IOwait hanging system"
date: 2005-02-15
forum: General Help
---

### Post by nocturn on 2005-02-15
Since friday, my wife's system is behaving very weird.

All of a sudden it lost nework connection, saying the IRQ of the network card was claimed by another device (nothing was changed).

Rebooting did not fix anything, so on saturday I booted a LiveCD and it was fine.  Rebooting the installed system also worked again.

So, it was fine until yesterday.  My wife said her system had been slow all day.  I just checked top and dmesg before shutting it down (it was valentine ;-) )

dmesg had nothing to report, but top showed me something very unusual.  The system had 0% idle time.  All CPU time was going to wait (90%) and sys (10%).
There was no process doing anything at that time.

Coming to think of it, last week I installed the the latest kernel fix on her system, but it could also be a hardware failure...

Her system is:
Athlon (thunderbird) 1.4
ECS board with VIA KT133 chipset 
256 MB SDRAM
40 GB IBM DeskStar
Very old HP CDRW
24x phillips CDROM
3Com 100Mbit NIC
Running Ubuntu Warty

Has anyone experienced something like this?  Any tips?

---

### Post by nocturn on 2005-02-16
I think I found the cause of the problems.

Yesterday, another  popped up, so I checked the temperature in the BIOS.
It reported 59°C CPU and 40°C System, way to high.

The system overheating causing all sort of weird errors.  I hope everything will be fine after removing dust from the fans and adding a case-fan.

---

