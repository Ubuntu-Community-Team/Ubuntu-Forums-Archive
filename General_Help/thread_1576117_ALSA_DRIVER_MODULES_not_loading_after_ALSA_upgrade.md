---
title: "ALSA DRIVER MODULES not loading after ALSA upgrade RT-kernel-33"
date: 2010-09-16
forum: General Help
---

### Post by Vigh on 2010-09-16
Hi,
 my alsa driver modules are not loading following an upgrade to alsa-1.0.23, I am running real-time kernel 33, the latest, my distribution is Maverick Meerkat, alsa-1.0.23 is working perfectly on the generic kernel, but not on the real-time kernel, as the real-time kernel is based on lucid kernel i think. Is there a way to use old lucid alsa modules and load them for my real-time kernel 33. 

Or get my soundcards detected. aplay -l results in no sound cards detected for the realtime kernel, working perfectly on generic kernel.

Regards

Ant

---

### Post by Vigh on 2010-09-17
Changed to KERNEL35-generic, no problems now.

---

