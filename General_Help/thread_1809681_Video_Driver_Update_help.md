---
title: "Video Driver Update help"
date: 2011-07-21
forum: General Help
---

### Post by Williamk13 on 2011-07-21
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

I cant find the driver updates or whatevr for this, and i need it for play on linux! Can anybody help?

---

### Post by UCSBGauchosRock on 2011-07-21
Have you checked the "Additional Drivers" option under the menu? I have not had much experience tweaking Intel Integrated Video Drivers under Ubuntu but it may have a proprietary driver there that has not been activated.

---

### Post by Williamk13 on 2011-07-21
Yeah i checked i dont have any additional drivers..

---

### Post by UCSBGauchosRock on 2011-07-21
Hmmm the one thing that I can suggest is going to Intel's web site and browsing their drivers for the one that most closely or perfectly matches yours. 

Before that however, could you try the command "sudo apt-get install xserver-xorg-video-intel" without the quotes? It could be possible the package is not installed and therefore your drivers are not present but the situation is unlikely.

EDIT: Also be sure that all of your software sources are checked(aside from source code) in Synaptic Package Manager ----> Settings -----> Repositories

---

