---
title: "Odd Nvidia problem - driver loads but fails to work"
date: 2009-07-09
forum: General Help
---

### Post by ThaddeusW on 2009-07-09
This is a real tough one for me. I recently had some kernel trouble but fixed the problem. Then the darn sound stopped working but I fixed it. But once the sound was fixed the nvidia driver no longer works. I am running Ubuntu 8.04

The nividia problem popped up after I installed the restricted module package to try and remedy my sound problem. It worked but then my nvidia driver would not work. GDM would attempt to start but instead of going from the graphical boot screen with progress bar it would drop to the terminal but flicker a few times them X would come up with a warning that I am running in low graphics mode. I then rebooted, told grub to load the recovery mode and reset the X configuration. I figured that the Nvidia driver somehow was broken. I downloaded the latest version 185.18.14 and ran it with the --uninstall option to purge the old driver and then ran it again to install the new driver. It worked with no errors so I started GDM and the same problem happened again. The screen flickers and then goes into low graphics mode.

My next move was to drop to a real console and kill GDM and then type startx which starts my old fluxbox desktop. And wouldn't you know it, X starts with the nvidia driver!

So I test the Driver by running GLX gears and get frame rates over ten thousand. I then exit X and restart from the command line. But once again GDM cannot start the Nvidia driver and drops to low graphics mode.

Uninstalling and reinstalling the driver did not work either. So my next move was to look a the Xorg logs in /var/log but nothing shows up in any of the logs. no errors that it cannot start the driver. 

So my question is has anyone ever ran into this problem and are there any ways I can start GDM in a debug mode to watch for problems? It just doesn't make sense that startx in a terminal runs the driver but GDM cannot. It used to work but now for some unknown reason it does not.

---

