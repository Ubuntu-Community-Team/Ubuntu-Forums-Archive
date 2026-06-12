---
title: "Just started with Ubuntu, can't get monitors to work"
date: 2010-11-16
forum: General Help
---

### Post by chaz42 on 2010-11-16
I have two monitors, they both show up as unknown, and I can't enable dual monitor support. I've been searching online for a solution, but keep coming across "dpkg reconfigure xserver-xorg" which apparently does not work in the newest version of ubuntu. 

Other methods I've found don't seem to work either. I have a Samsung Syncmaster 226BW and a Gateway FPD1530.

---

### Post by chaz42 on 2010-11-17
Wow, still no response...?

Don't mean to be crass, but if you look at my join date, I last gave Linux a shot over a year ago. The learning curve is a bit steep for me and it's tough to stick with it when I can't get displays to work correctly.

I'd really appreciate some advice...

---

### Post by JDorfler on 2010-11-17
Never had any problems with Syncmasters, but I don't know about the Gateway.  What video card are you using and what type of connection?

---

### Post by chaz42 on 2010-11-17
Ati Radeon HD 4570. Samsung connected DVI, and Gateway is connected with VGA -> DVI adapter. 

When the Gateway is unplugged, the Samsung shows up as "Unknown" and is limited to 1400 x 1050 instead of the 1650 x 1200 resolution it should display at.

---

### Post by Vigh on 2010-11-17
enable proprietary graphics card drivers

system- administration-> additional drivers

reboot

use your graphics card tool to set up the dual monitor system

---

### Post by chaz42 on 2010-11-18
> **Vigh said:**
> enable proprietary graphics card drivers

system- administration-> additional drivers

reboot

use your graphics card tool to set up the dual monitor system

How do I use the graphics card tool?

---

### Post by kwhatcher on 2010-11-18
Are you referring to the ATI tool?

---

### Post by JDorfler on 2010-11-18
> **kwhatcher said:**
> Are you referring to the ATI tool?

Also known as the Catalyst Control Center.  If you installed your drivers correctly you will have two CCCs under your preferences main menu.  One is regular CCC and one is Admin.  Here you can work on getting your settings correct.

---

### Post by chaz42 on 2010-11-19
> **JDorfler said:**
> Also known as the Catalyst Control Center.  If you installed your drivers correctly you will have two CCCs under your preferences main menu.  One is regular CCC and one is Admin.  Here you can work on getting your settings correct.

This worked, thank you, although there is a strange issue of there being four menu items of Catalyst Control Center. I don't want to touch it because the multiple monitors are working... for now.

---

