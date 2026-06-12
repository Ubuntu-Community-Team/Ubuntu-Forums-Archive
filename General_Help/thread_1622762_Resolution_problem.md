---
title: "Resolution problem"
date: 2010-11-15
forum: General Help
---

### Post by Rhodan on 2010-11-15
I have a Dell U2311H monitor which has a native resolution of 1920 x 1080. My graphics card is an ATI 6870.

Last night I installed Ubuntu 10.10 alongside my Windows installation, and when booting into Ubuntu, the maximum resolution I can select is 1280 x 1024. 

How can I resolve this to get Ubuntu to display at the native resolution?

---

### Post by clhsharky on 2010-11-15
Rhodan

Have you installed ATI proprietary drivers(fglrx)?

Sharky

---

### Post by Rhodan on 2010-11-15
Hi,

No, I basically just installed Ubuntu, rebooted and then had a quick look around. 

Tonight I'll install the ATI drivers. Will that fix it?

---

### Post by clhsharky on 2010-11-15
Rhodan

Yes it should.

System> Administration>Hardware Drivers
Select/activate/restart

Sharky

---

### Post by racie on 2010-11-15
Yep.  It should be under System > Administration > Hardware Drivers.  Or there may be a little green icon in the upper-right corner of your screen.

*edit*  Whoops.  Too slow.  :/

---

### Post by Rhodan on 2010-11-16
OK I installed the driver as mentioned above, but after the reboot the screen is just black?

Idea's?

---

### Post by Rhodan on 2010-11-16
If I boot into safemode and uninstall the ATI driver then the display comes back, back limited to 1280 x 1024.

Appreciate any replies to solve this.

---

### Post by racie on 2010-11-16
Did you install the current recommended driver?  Try installing a different version if you are given the option to do so.

---

### Post by GSF on 2011-01-08
> **Rhodan said:**
> OK I installed the driver as mentioned above, but after the reboot the screen is just black?

Idea's?

hello, i have the same display and graphics card, and seem to get the same black screen... any ideas how to fix it?? thanks

---

### Post by arzali on 2011-01-08
Try Ctrl+Alt+"Numpad minus".
my screen gets black because of unsupported resolutions and this changes it to a lower resolution, after that i set my desired resolution with the display setting

---

### Post by Dnabb10 on 2011-01-09
I'm having this same problem. I try to install the proprietary driver in System->Administration->Additional Drivers, but when I install it and reboot, I get a black screen and my computer freezes. 

System Specs:
AMD Phenom X4 955 BE
ATI 6870
Crosshair III
WD 1 TB Caviar Black 
2gb x2 Gskill Ram

It also limits me to 1600x1200 resolution when my monitor is optimized at 1920x2000

---

### Post by GSF on 2011-01-09
> **arzali said:**
> Try Ctrl+Alt+"Numpad minus".
my screen gets black because of unsupported resolutions and this changes it to a lower resolution, after that i set my desired resolution with the display setting

tried this, but doesnt work... maybe the driver that comes with ubuntu doesnt support 6870..??

---

