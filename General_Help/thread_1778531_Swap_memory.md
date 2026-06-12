---
title: "Swap memory"
date: 2011-06-09
forum: General Help
---

### Post by ccm.vslam on 2011-06-09
Hi,

Is it normal to have 0 swap memory? I get this when I type free-m

             total       used       free     shared    buffers     cached
Mem:          1001        671        329          0         17        294
-/+ buffers/cache:        359        641
Swap:            0          0          0

I have been trying to rosmake a package but everytime when it reaches a certain point, the computer "hangs"(lags really really slowly, and cannot switch windows otherwise it will become even worse). After that an error pops up saying it fails to make a particular package then it continues on as per normal with the rest of the packages.

I also noticed when it hangs the wa% in the terminal running "top" is very high when the computer "hangs"

Does anyone know what the problem might be and how do I fix it? I'm running on Ubuntu 10.4. Thanks a lot.

---

### Post by kerry_s on 2011-06-09
You have no swap active according to "Swap: 0 0 0"

did you make a swap partition?

a quick fix is to install dynamic swap. i recommend "swapspace", it's what i use. just install, no real need to mess with the settings.

---

### Post by prshah on 2011-06-09
> **ccm.vslam said:**
> 
Is it normal to have 0 swap memory?
Swap:            0          0          0

Does anyone know what the problem might be and how do I fix it?

Nope, it's not normal to have 0 swap memory.

You can activate swap partitions (if you have any) with the command```
sudo swapon -a
``` After this command, if swap available still shows "0" then you probably have no swap partitions.

At this point, you have two choices; either make a swap partition, or make a swap file (easier). Please post back if you want more details on either.

---

