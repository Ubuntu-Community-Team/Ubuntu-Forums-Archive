---
title: "Nouveau fails on alternate restarts"
date: 2010-07-25
forum: General Help
---

### Post by mfseeker on 2010-07-25
I am running Lucid happily, but when I restart, I am forced into low-res.

If and only if I issue "sudo aptitude update && sudo aptitude install xserver-xorg-video-nouveau", then when I restart the next time, nouveau loads properly.

Successive restarts without this aptitude command give me nothing but low-res restarts. Sometimes I need a second  "sudo aptitude update && sudo aptitude install xserver-xorg-video-nouveau" followed by a restart before hi-res is restored.

I have tried many times over the months to install the Nvidia proprietary driver, but I have given up. There are doubtless bits and pieces of the nvidia installations left behind, though I have run Synaptic's "Complete Removal" on packages containing "nvidia" in their name. I hesitate to purge the system of all files with names containing "nvidia" since I have been led to believe that some of these may be essential for nouveau. In addition, I suspect there may be other files left behind by the abortive nvidia installation attempts that do not have "nvidia" in their names, and that one or another of these might be causing my problem.

I would just like to run a clean, reliable nouveau every time I reboot.

---

