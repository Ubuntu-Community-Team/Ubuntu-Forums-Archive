---
title: "Cooking egg rolls on my laptop its so hot"
date: 2011-01-31
forum: General Help
---

### Post by TheHackOps on 2011-01-31
Not rly but i recently installed ubuntu desktop edition on my friends laptop 4 install tries later and boom we have lift off, all engines are a go. 3 days later my friend tells me his laptop is getting so hot he can cook his egg rolls on it (Hes korean what do you expect) and every 10 or so minutes it freezes.

1. Could this be because i used the wrong remix of ubuntu (Dekstop and not netbook)
2. Is there a tweak or thing i can do to resolve this
3. FYI it was not this hot with winblows
4. Why am i the only one without major issues ever with ubuntu :guitar:

---

### Post by skytreader on 2011-01-31
What are the specs of the laptop? Is it a laptop or a netbook? Netbooks have considerably less powerful hardware. On my laptop (Gateway, AMD Turion64), I install the Desktop edition and its fine.

---

### Post by Quackers on 2011-01-31
Is the fan working? The freezes could be caused by overheating. I would suggest that he doesn't use it for the moment. What is the make/model of the machine? Graphics card model? There are several possible causes, but the first concern should be to not damage the machine.

---

### Post by Habitual on 2011-01-31
I'd like to suggest cleaning out the computer, literally. It could have accumulated some dust-bunnies.

---

### Post by BlackLab on 2011-01-31
A friend of mine reported that their laptop was continually shutting down. I figured overheating, so I ran it for a while, no shutting down. ... anyway I blew the dust out of the processor fan anyway. Well that did not work .. turned out the user sits the laptop on lap, and their leg completely blocking the air intake for the processor. So it was not dust, it was a fat thigh causing the laptop to overheat and shutdown frequently. Shutting down is simply the laptop's way to prevent the processor being damaged with heat. Now, the user places the laptop on a table top to allow enough air into the processor .. Problem solved .. I on the other hand just make sure my laptop's air intake is not covered by my leg when I hold it on my lap.

---

### Post by nd456 on 2011-01-31
Maybe a cooling pad would help

---

### Post by peculiar penguin on 2011-02-01
Make sure the fan still works and air intakes/vents are clear. If the cooling system is clogged with dust/food crumbs/whatever it needs to be cleaned out.

Install and run powertop, check its output to make sure the CPU clocks down and enters low power states (C2, C3,...) when idle. If that's not the case, experiment with kernel parameters (my Samsung Laptop needs the noapic parameter, or it will burn endless CPU cycles despite doing nothing).

If it has a dedicated video card, look into power management options for that.

---

### Post by TheHackOps on 2011-02-01
No i know its the over heating, When i applied my "Turbo LapPad" Cooler which is amazing. It is verry cool and NO FREEZING WHAT SO EVER. The design is pretty **** ill admit. BTW Its a notebook with high specs ill get them later thanks guys

---

### Post by BlackLab on 2011-02-01
> **TheHackOps said:**
> No i know its the over heating, When i applied my "Turbo LapPad" Cooler which is amazing. It is verry cool and NO FREEZING WHAT SO EVER. The design is pretty **** ill admit. BTW Its a notebook with high specs ill get them later thanks guys

Are you sure it does ~not~ overheat when running Windows? All it might take is to watch a video in media player, and restrict the notebook's ventilation. The other question I have is what is the user doing in Ubuntu when the notebook overheats?

In any case all you can do is clean the insides, particularly the CPU fan and heat sink with compressed air .. same goes for the graphics card if it has a fan.

---

### Post by quadproc on 2011-02-01
> **TheHackOps said:**
> Not rly but i recently installed ubuntu desktop edition on my friends laptop 4 install tries later and boom we have lift off, all engines are a go. 3 days later my friend tells me his laptop is getting so hot he can cook his egg rolls on it (Hes korean what do you expect) and every 10 or so minutes it freezes.

Which Ubuntu version is in use?  I ask because there is a known problem with 10.04 where the operating system would sometimes get into a loop while looking for something to do; this would cause the CPU usage to go to 100% and that draws a lot of power and generates a lot of heat.

The 10.04 "spin" problem was fixed in the kernel; sorry, I don't remember offhand which versions had the problem and which did not.

quadproc

---

### Post by TheHackOps on 2011-02-04
10.10, Ubuntu Desktop

---

