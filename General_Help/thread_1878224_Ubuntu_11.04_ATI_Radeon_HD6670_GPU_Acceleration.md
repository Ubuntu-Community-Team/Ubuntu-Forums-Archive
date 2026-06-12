---
title: "Ubuntu 11.04 ATI Radeon HD6670 GPU Acceleration"
date: 2011-11-09
forum: General Help
---

### Post by High Current on 2011-11-09
My CPU usage is high when just moving windows about the screen. This suggests to me I may have not correctly installed my graphics card or something has not been configured properly.
Also I have noticed I cannot play HD clips on youtube so I fear that the GPU is not kicking in when its supposed to.


My GPU is a Sapphire Radeon HD 6670 1GB
Pentium 4 Processor 3.00GHZ HyperThreading
2GB DDR2 @ 800MHZ

Any help will be much appreciated.

---

### Post by Mark Phelps on 2011-11-09
If the GPU was not "kicking in", you would have NO video.

You're most probably running off the default open-source drivers, which with my HD 4290, I found were not very good back in 11.04.

To confirm that, you can open a terminal and enter "fglrxinfo".  If the restricted drivers are installed, you will get several lines providing you version information.  If not, you'll probably get an error about not being able to find "fglrxinfo".

To install the drivers, you would use Additional Drivers.  It should offer you the AMD restricted drivers.

You can also go the the AMD driver site and download the Catalyst 11.10 drivers yourself.  The file you download will have instructions about how to install them.

---

### Post by High Current on 2011-11-14
fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6670
OpenGL version string: 4.1.11161 Compatibility Profile Context

From this I assume its installed correctly but in my additional drivers I have the proprietary FGLRX Graphics driver activated and currently in use. I see Catalyst Control Centre in the system settings page but still my computer CPU usage is high...

---

### Post by Mark Phelps on 2011-11-14
You're correct ... the fglrxinfo results confirm that the restricted drivers are installed.

But, your statements are confusing ...

Your title mentions GPU usage (graphics chip) but your latest reply mentions CPU usage (processor chip).

If CPU usage is high, that is likely unrelated to using the restricted drivers.  And, since that is a very different problem, you would do better starting a new thread to address that.

---

