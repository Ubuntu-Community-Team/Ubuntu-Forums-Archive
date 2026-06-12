---
title: "nVidia Card in 10.04 w/ DVI connected monitor won't load GDM"
date: 2010-06-04
forum: General Help
---

### Post by Despotic on 2010-06-04
Hello, I am at the end of my leash here.
I've gone through so many posts that seem to be the same problem, but doing everything everyone else is doing with success, is leaving me discouraged.
This machine was FANTASTIC with 8.04 and I upgraded for Cisco AnyConnect compatibility in the office :(

I have a LOW end nVidia AGP card, a 6000 line (6200, 6800?) and I have a Samsung SyncMaster 205BW plugged in via DVI. If I plug my monitor in through the analog plug, everything seems to work fine.

When I boot via DVI plugged monitor,  I get "Fatal server error: no screens found" but more importantly "NVIDIA(0) Failed to initialize the NVIDIA graphics device! Screen(s) found, but none have a usable configuration."

I've uninstalled and reinstalled and updated nouveau, nvidia-current, grub as well as blacklisted all recommended devices.

I did NOT upgrade form 8.04, I did a fresh 10.04 install because I initially did upgrade and it failed. There is definitely no outdated pieces left because I even swapped the hard drive for a clean one.

I appreciate any help you can provide. If there is some utilities I can run to give you an idea of what's installed or not, I'm all ears. I still don't know all these diagnostic commands by memory yet.

When I uninstall all of the nVidia drivers, I do boot to Gnome fine and everything looks great, but I can't configure my monitor because I'm not using a proprietary driver and I can't turn on Visual Effects.

---

### Post by dcstar on 2010-06-05
> **Despotic said:**
> 
..........
When I uninstall all of the nVidia drivers, I do boot to Gnome fine and everything looks great, but I can't configure my monitor because I'm not using a proprietary driver and I can't turn on Visual Effects.

Old Nvidia chips are not supported on later Linux releases (not just Ubuntu).

If you have an old unsupported chipset then you either use on older version of Ubuntu or live with the open source driver.

---

### Post by wojox on 2010-06-05
Double Post

---

### Post by wojox on 2010-06-05
> **dcstar said:**
> Old Nvidia chips are not supported on later Linux releases (not just Ubuntu).

If you have an old unsupported chipset then you either use on older version of Ubuntu or live with the open source driver.

Yes that is what I had to do. Open source driver. I have same chipset.

---

