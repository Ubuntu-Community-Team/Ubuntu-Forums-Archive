---
title: "Nvidia drivers not working after 11.10 (64 bits) clean install, getting desperate"
date: 2011-10-25
forum: General Help
---

### Post by Panna-cakkhu on 2011-10-25
After a clean install of Ubuntu 11.10 (64 bits) i kept ended up in a black screen (no X, no lightdm, no nothing). 

I fixed that part by removing the Nvidia drivers. (For those who have the same problem, here is what i did: boot in recovery mode and entered the following command from the root prompt: apt-get --purge remove nvidia-current)

Then when rebooting i could login. The feeling was great but that didn't last. I couldn't install any version of the nvidia drivers to get them to work:
- additional proprietary drivers proposed by ubuntu: freeze at booting
- new purge and drivers from ubuntu-x-swat/x-updates repository: freeze at booting
- new purge and vidia-173 drivers: doesn't work
- new purge and nvidia drivers from nvidia website (64-bits version): no success either

Any help would be GREATLY appreciated

System: Ubuntu 11.10 64 bits fresh install, Nvidia GTX 560

---

