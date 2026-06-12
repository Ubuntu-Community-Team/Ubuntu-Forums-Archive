---
title: "Java is using massive CPU"
date: 2011-08-12
forum: General Help
---

### Post by Spyderkid on 2011-08-12
i run minecraft with java and it uses massive CPU up to 60%

Java is dedicated almost 1GB of my 4GB RAM
i have a cheap AMD quad core proccessor (i think its equivilant to dell i3 or dell dual-core.)


anyone got any ideas?

---

### Post by The Cog on 2011-08-12
I would expect any graphical game to use the CPU fairly heavily. 60% suggests that minecraft is using 2 threads on your quad-core. I don't actually think there is a problem here.

---

### Post by LinuxSavedMyComputer on 2011-08-12
Also Minecraft runs P-code in a virtual machine. Java needs to translate it's code into machine code, so it would take more resources

---

### Post by Spyderkid on 2011-08-12
hmm... ok

i really badly need a better graphics processor though. that's probably what makes it seems laggy in game.
ive only got an awfull built in one at the moment

---

### Post by hookitup on 2011-08-18
I have the same issue but one of my cpu's spikes to 100%.

Its a dell latitude E6400, Intel Core 2 Duo CPU P8600  @ 2.40GHz, 2gb ram, 80gb HD


any idea anybody ?

 i read something on [this page]("https://www.pingidentity.com/support/solutions/index.cfm/Java-CPU-usage-at-100-percent") but not 100% sure what to do with this info.

---

### Post by SavageWolf on 2011-08-18
I would expect MineCraft to use up that kind of resources, it may not look like it, but it's very graphics and map-generatey intensive (And also single threaded, but that's on Notch's todo list). I expect that there may be performance boosts soon.

---

