---
title: "3 restarts required to boot?"
date: 2011-09-28
forum: General Help
---

### Post by mattf87 on 2011-09-28
Hi,
   I have just installed Ubuntu 11 on to my shuttle PC box. The HDD was new and Ubuntu is the only OS on it. Once booted the OS perfumes really well and i'm very impressed with Ubuntu.

However I do have an issue trying to get it to boot properly. Every time I come to use the machine after it has been shut down it requires me to press the restart button three times.

- First attempt: The system freezes with a blank purple screen and all HDD activity stops.

- Hit restart: The system loads as far as the GRUB interface offering me a number of boot options, I select the top one (ubuntu 11 with linux...) and the system goes to a black screen with a flashing cursor. It then freezes and all activity stops.

- Hit restart again: The systems boots to the GRUB interface and then boots correctly to my system. 

Once it's up I get no problems at all.

Any advice would be appreciated, i've tried using "boot repair" with the option to reinstall grub but I still get the issue.

Thanks

---

### Post by mcduck on 2011-09-28
Such booting problems are usually a result from hardware problems, most likely related to either your motherboard or power supply.

Check that all cables are properly connected, and that there are no visibly broken, bleeding or bulging capacitors anywhere. If you could possibly get access to a replacement PSU and/or motherboard, it would of course help a lot to see how swapping one of the components helps.

---

