---
title: "Dynamically changing allowed CPU C-states"
date: 2009-12-19
forum: General Help
---

### Post by Morientes on 2009-12-19
Is there a way in Ubuntu 9.10 to dynamically (that is, without restart) change which C-states the processor is allowed to go into?


The reason I want to do it, is because my CPU suffers from the "whining" noise when in C-states 3 and 4 and thus I sometimes need to prevent it from going into these states to be able to use the computer.

I am able to do it via grub now. It works fine to eliminate the sound. But sometimes I want the battery to last longer and would prefer to be able to allow the processor to go to c-state 4 without rebooting.
Is this possible?

And do anyone know what the cost to battery life is when preventing the CPU from entering the higher c-states? Because if we are only talking about maybe 20 minutes or so then it doesn't matter much...

---

### Post by Morientes on 2009-12-21
Anyone?

---

### Post by Morientes on 2010-01-10
So this is not possible or?

---

### Post by happyhamster on 2010-01-10
Right-click your top panel, and choose "Add to Panel" and then "CPU Frequency Scaling Monitor". When you left-click that applet, you'll get a list of CPU-Frequency governors (Ondemand, Performance, etc) you can choose from, or even select the frequency manually.

---

### Post by Morientes on 2010-02-26
Thank you! I will try that...

---

