---
title: "i need HELP! how install nvidia driver Sony vaio vpc f126"
date: 2010-12-13
forum: General Help
---

### Post by lordsaga69 on 2010-12-13
hello everybody i need help, i just installed Ubuntu 10.10 to my sony vpcf126, but when i turn on the nvidia driver for the higher graffics, and when i restard the laptop i get the black screen and i can not do anything. what are your recommendation ?by the way the nvidia card that is installed is : NVIDIA GeForce GT 330M graphics

i'll appreciated...

thanks..

---

### Post by Krytarik on 2010-12-13
1.) Did you install the proprietary drivers via "System -> Administration -> Additional Drivers"?

2.) Save the configuration to the "xorg.conf":
- go to "System -> Administration -> NVIDIA X Server Settings"
- click at "X Server Display Configuration" on the left side
- check/choose your desired configuration (it doesn't matter if the displayed monitor is not exactly yours)
- click at "Save to X Configuration File"
- enter your "root"-password when asked
- choose replace, not merge!

---

