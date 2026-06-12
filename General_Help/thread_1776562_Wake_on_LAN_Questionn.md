---
title: "Wake on LAN Questionn"
date: 2011-06-06
forum: General Help
---

### Post by AngryMallard on 2011-06-06
So I am running 11.04 and am trying to set up WoL and I have gotten it to work, but only if I mmanually click "suspend" on the top right icon on the toolbar. Ideally I would also like to wake on LAN if the computer automatically suspends itself after an hour (power settings). Currently it will not wake if it automatically suspends. What is the difference between manual and automatic suspend? What should I do to get WoL to work all the time?

---

### Post by pqwoerituytrueiwoq on 2011-06-06
it needs to be enabled in bios and ubuntu
[http://ubuntuforums.org/showthread.php?t=1684050](http://ubuntuforums.org/showthread.php?t=1684050)

---

### Post by AngryMallard on 2011-06-06
It is. Like I said, WoL WORKS when I physically click on "Stand By" and then send a magic packet to the computer, but it does NOT work if I set the computer to go to Stand By after an hour of inactivity and then send the same packet. What's the difference?

---

### Post by atca on 2011-07-16
> **AngryMallard said:**
> It is. Like I said, WoL WORKS when I physically click on "Stand By" and then send a magic packet to the computer, but it does NOT work if I set the computer to go to Stand By after an hour of inactivity and then send the same packet. What's the difference?

its most likely your router/switch clearing the ARP cache entries after a short amount of time.

---

### Post by tgalati4 on 2011-07-17
sudo apt-get install acpitool
man acpitool
acpitool -w

Make sure that the bus device that controls the network card (probably one of the pci ports) remains enabled (powered) during suspend.  It's possible that depending on how you suspend, it stays awake with one method and goes to sleep with the other.

---

