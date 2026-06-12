---
title: "Latest kernel problems"
date: 2010-10-10
forum: General Help
---

### Post by coldraven on 2010-10-10
Two days ago the Update Manager installed kernel 2.6.32-25
After a re-boot Suspend is broken, it takes about 30 seconds to suspend and will not recover.
Also the wi-fi won't work at all.
Booting with the previous kernel I have no problems.
Has this happened to anyone else ?
I was thinking of installing 10.10 64bit, I wonder if it will work! 

Ubuntu 10.04 32bit
Compaq 6715b laptop, 2x Turion, 4GB ram, Broadcom wi-fi, ATI X1250 graphics

---

### Post by claracc on 2010-10-10
Recently I upgraded to Lucid Lynx form Karmic Koala (for me, the best linux distro till now), linux kernel 2.6.32-25 in hp compaq 6720 S laptop with Intel Corporation PRO/Wireless 3945ABG [Golan] wifi card and Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c).

Now, when I close the lid of laptop it doesn't suspend as it is marked in power manager, I have to suspend from xterm : sudo pm-suspend. In karmic koala it worked.

Network manager gnome keeps the wifi connecting/disconnecting all the time ( wifi unusable), I had to install wicd, after some workarounds, it fixed wifi, working now.

---

### Post by coldraven on 2010-10-10
> Now, when I close the lid of laptop it doesn't suspend as it is marked in power manager

There is a strange bug in the power manager GUI.
When I first looked at it there was no option to switch off the screen, only suspend or hibernate.
The missing option was not in the drop down list unless I scrolled UP the list if that makes sense.
In other words it was hidden from view. I wonder if you try selecting each option and see if it works properly afterwards.
I like to listen to internet radio with the lid closed and it works fine now.

---

