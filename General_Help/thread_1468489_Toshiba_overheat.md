---
title: "Toshiba overheat"
date: 2010-05-01
forum: General Help
---

### Post by killerpi on 2010-05-01
I am running Ubuntu 10.04, but was running 9.10 for a couple of months.  In all that time my laptop runs really hot, mostly near 70C is a normal temp. As such I  have a big problem with overheating then sudden shut down. After looking  all over in various forums I think its a problem with my fan not running fast enough or just not richt, but  I cannot find a good fix. I need a step-by-step fix if anyone has one. Can anyone help? Laptop: Toshiba Satellite  L300

---

### Post by BrokeMahPC on 2010-05-01
It's problem with the Linux Kernel - KMS - Video Drivers.
There is currently a lack of Dynamic Power Management available under KMS.
What video card do you have and what driver are you using?
There are a couple of things to try to solve it - if you have ATI I can probably help.

To determine your video card manufacturer, execute the following in the console or a terminal window:
```
lspci | grep VGA
```For ATI cards:
If you are running radeon and KMS (Kernel mode setting)try:
-boot up with user modesetting rather than kernel modesetting by  typing something like radeon.modeset=0 at boot time, 
-press e at the grub screen,
"quiet splash radeon.modeset=0"
It should look like this ^
-then maybe adding the ForceLowPowerMode  option to your xorg.conf. 
toshiba overheating problems here:
[http://ubuntuforums.org/showthread.php?t=1456703](http://ubuntuforums.org/showthread.php?t=1456703)
other examples:
[http://www.phoronix.com/forums/showthread.php?t=23227](http://www.phoronix.com/forums/showthread.php?t=23227)
[http://ubuntuforums.org/archive/index.php/t-1418133.html](http://ubuntuforums.org/archive/index.php/t-1418133.html)

---

