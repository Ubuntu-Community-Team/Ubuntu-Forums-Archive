---
title: "Ubuntu not booting! HELP!!"
date: 2010-08-25
forum: General Help
---

### Post by squidpotion on 2010-08-25
A little background info. - I was fiddling with Ubuntu to get my graphics card to work (NVIDIA GeForce 8200), trying to enable compositing for Docky and Compiz, and I was having a REALLY hard time trying to get it to work. I tried installing from Synaptic, from the terminal, from outside the GUI... Everytime I installed the drivers, the resolution would be HUGE and I couldn't change it from Ubuntu or from NVIDIA. If I uninstalled everything NVIDIA and restarted, it would run in low graphics mode and the resolution would be back to normal, but Docky would be kind of laggy. The desktop effects part of Appearance would be grayed out too, so I couldn't select it at all. 

So I tried installing the drivers again (ver. 256.44) and restarted, and now Ubuntu freezes at the splash screen. If I press alt+ctrl+del, it restarts, but that's it. I tried alt+ctrl+F1, to maybe start the GUI, but that doesn't work either. 

Can someone PLEASSSEEE help me fix this mess? Much thanks in advance!

---

### Post by Quackers on 2010-08-25
Try holding down the shify button whilst booting. You may then get the option to start in recovery (safe) mode.
Did you get the Nvidia driver from Nvidia or from System > Admin > Hardware Drivers?

---

### Post by squidpotion on 2010-08-25
I tried the official driver and the one from Synaptic/xswat.

Ok. I booted to recovery mode, tried uninstalling the driver and when I did I got this:

You appear to be running runlevel1; this may cause problems. For  example: some distributions that use devfs do not run the devfs daemon  in runlevel 1, making it difficult for 'nvidia-installer' to correctly  setup the kernel module configuration files. It is recommended that you  quit installation now and switch to runlevel 3 ('telnit 3') before  installing.

The first time I got that, I just said "eff it" and uninstalled anyway  and then rebooted. Still stuck at the splash screen. Rebooted again, and  then tried purging nvidia by entering 

```
sudo apt-get remove --purge nvidia*
```Got some text like it  was working, which ended in "could not find file 'nvidia*'. Hmph.

I also don't have "Hardware Drivers" under Administration, for whatever  reason. I remember looking for that when I was trying to get it working  right the first time.

Anything else I can do?

---

