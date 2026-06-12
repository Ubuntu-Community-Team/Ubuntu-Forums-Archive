---
title: "system clock shows dec 31 2004 on startup"
date: 2006-02-24
forum: General Help
---

### Post by shiroma on 2006-02-24
everytime i start the computer i think the computer tries to sync the clock with what the internet says. i use wpasupplement and i have to reactivate the wireless card after gnome starts up. how can i have the internet work brfore the computer syncs with the internet clock?

---

### Post by o_fortuna on 2006-02-24
[QUOTE=shiroma]everytime i start the computer i think the computer tries to sync the clock with what the internet says. i use wpasupplement and i have to reactivate the wireless card after gnome starts up. how can i have the internet work brfore the computer syncs with the internet clock?[/QUOTE]
If your internet wasn't working, it would simply fail to find the ntp site and sync the clock. There might be a problem with the battery in your computer (which keeps the clock running when the computer's off). Have you tried going in to the BIOS (probably DEL at startup) to see if the clock is set correctly (after setting it from within Ubuntu)?

As for your question, there is probably a script in /etc/init.d that controls the ntp sync. I don't know how to change the order, but you could always have a look at [this]("http://www.ubuntuforums.org/showthread.php?t=80423") which will help you modify init scripts and may even help you solve the problem.

---

