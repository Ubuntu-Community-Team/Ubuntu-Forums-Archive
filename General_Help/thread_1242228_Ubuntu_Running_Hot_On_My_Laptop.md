---
title: "Ubuntu Running Hot On My Laptop"
date: 2009-08-16
forum: General Help
---

### Post by jschille on 2009-08-16
I did some searching through the forums and found that someone said to add the command

sudo sysctl vm.swappiness=0

It seemed that it works, is that a safe line to run?

---

### Post by earthpigg on 2009-08-16
the majority of the time, my experience has been that when ubuntu runs hot on a laptop it is because some program is using CPU cycles needlessly. the solution you mention above looks a bit like overkill.

run this in a terminal, and see if there is a program sitting at like 50% of CPU% for no good reason:

> top

---

### Post by tom.swartz07 on 2009-08-17
Hi all

Just out of pure curiosity and want to learn more, what exactly does that command do?

sudo sysctl vm.swappiness=0


My laptop tends to run very hot sometimes, and in the past few days, Ive actually walked in on it just as the safety overheat kill activated. 

To the best of my knowledge, there were no programs trashing the CPU, but the only culprit that MIGHT lead to the CPU topping off would be Gnome Do.

Im just curious as to what the command does- does it limit the CPU cycles, or 'throttle' the CPU back, etc?

Thanks!

---

