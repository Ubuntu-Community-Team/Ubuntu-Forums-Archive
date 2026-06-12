---
title: "Intel G33 video resolution Karmic"
date: 2010-01-25
forum: General Help
---

### Post by rationalisst on 2010-01-25
I recently did an upgrade from Jaunty to Karmic via the software updater. In the process I lost any screen resolution above 800x600. I'm running Karmic on a Dell Inspiron 530s desktop computer with Intel G33 onboard video. My monitor is  a Hanns-G HW191DP 19" LCD that has a maximum resolution of 1440x900. I've never achieved that resolution with this computer in either Windows Vista (which I have on another partition, sadly) or with previous versions of Ubuntu, but I have done better than 800x600. I believe with this computer I've been able to get 1280x768 at best (but I've attained the full 1400x900 resolution with other computers). I have searched for ways to improve the resolution in Karmic, but have had no luck. Any advice would be appreciated.

---

### Post by Geeke on 2010-01-25
Open a terminal,
sudo /etc/init.d/gdm stop (this then rolls back to the command line)
sudo X -configure (has to be a capital X)

Then do what it says on the screen

---

