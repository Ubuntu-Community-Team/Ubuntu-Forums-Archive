---
title: "Latest update from xorg-edgers nouveau driver fried my nvidia geforce 7600 card"
date: 2010-07-11
forum: General Help
---

### Post by chrissk_2 on 2010-07-11
Hi all,

at some point last week i updated my ubuntu installation and applied the latest xorg-edgers updates. This included some nouveau, mesa and gallium updates (i can not remember exactly).

When i rebooted the machine and compiz started, after a few seconds i had artifacts on the screen and everything was painted wrong. Then the system locked up. I rebooted and i could not log in since xorg could not start (the system was locking up). I rebooted again and i could see some blueish lines on the top of the screen during the grub boot screen. Also during normal boot the screen was all blue with some strange patterns. 

After a few unsuccessful reboots i tried rescue mode. This was successful and i had a fully working desktop but with software acceleration (llvmpipe). Modesetting was working perfectly. I checked the logs (xorg, dmesg) and i noticed a message about GPU lockup.

I tried the official nvidia drivers but the system was still locking up badly. I also had the same effect when i tried to boot on windows. 

The system is an 24'' imac with core duo 2 2.16Ghz, 4 GB ram and an nvidia 7600 GTX card.


Any help is appreciated

Thanks in advance

---

