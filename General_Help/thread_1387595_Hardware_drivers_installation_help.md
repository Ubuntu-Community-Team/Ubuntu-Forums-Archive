---
title: "Hardware drivers installation help"
date: 2010-01-22
forum: General Help
---

### Post by jffry09 on 2010-01-22
Hi.

I'm kinda new to Linux, and I'm having a problem with my hardware drivers. I have a laptop with an ATI Mobility Radeon HD 4570 graphics card, and I'm trying to download the hardware drivers so I can access 3D effects like Compiz Fusion. I'm using Ubuntu 9.1. When I try to install the drivers, the progress bar will go up a little and then get stuck in a spot. I try canceling the install and it won't work. Apt gets stuck as well, and I can't install packages from that point on unless I restart the computer. Is there some way I can download the hardware drivers so it'll work? Any help would be very appreciated. Thanks

---

### Post by bumanie on 2010-01-22
Go to System --> Administration --> Software Sources and ensure all check boxes are checked, **except** for the cd-rom box. The try again. If you have already done this - post back. If you are very new and don't understand the repository system, have a look [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by athevil on 2010-01-22
maybe this will help u

[http://ubuntuforums.org/showthread.php?t=1301327](http://ubuntuforums.org/showthread.php?t=1301327)

---

### Post by lordskid on 2010-01-22
Are you installing from Synaptic Package Manager?

try 
  sudo apt-get install xserver-xorg-video-radeon
from a terminal
It will allow using the 3d effects if that is all you are after. You can also try to download the binary from ati website and install it. But I believe it is not supported by Ubuntu.

---

### Post by jffry09 on 2010-01-22
Thanks a bunch! After I removed the CD from the list, Compiz started working. Why exactly was that preventing it?

---

