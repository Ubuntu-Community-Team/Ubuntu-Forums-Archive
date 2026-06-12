---
title: "Video Card Glitching Out"
date: 2010-07-05
forum: General Help
---

### Post by KarasuTengu on 2010-07-05
My video card just started glitching out.  Does anyone recognize the problem shown in the screenshot I have provided?

---

### Post by whych on 2010-07-05
Try setting a lower sync frequency.

---

### Post by fragos on 2010-07-05
Your glicthing appears only in the window of that application and not on the rest of the screen which may indicate your problem has nothing to do with the card. Do all applications you run look like this?

---

### Post by KarasuTengu on 2010-07-05
I only have two options for sync frequency: 60hz and auto.

--------

Its not just glitching in the app window. It seems to be all text.  IN the screen shot you can see that any text is glitched out.

---

### Post by fragos on 2010-07-05
Before buying a new graphics card I'd try running Ubuntu from the Live CD to see how the displays looks. If the Live CD is OK that would indicate a software or configuration problem on your system which might take a new clean install to fix. Try to back up your data before doing anything drastic.

---

### Post by KarasuTengu on 2010-07-05
> **fragos said:**
> Before buying a new graphics card I'd try running Ubuntu from the Live CD to see how the displays looks. If the Live CD is OK that would indicate a software or configuration problem on your system which might take a new clean install to fix. Try to back up your data before doing anything drastic.

With a live cd the display looks fine compared to the screenshot I posted, but there are some small pixel issues (random pixels are red or green).

This problem started when I first upgraded to the latest 9.10 kernel, then upgraded to ubuntu 10.04.  I had to reinstall the drivers for my video card, and then after the restart for the driver refresh, everything went bad.

---

### Post by fragos on 2010-07-05
I'm curious what video card you have. I highly recommend the "hardware Drivers" preference to install drivers. It avoids a lot of the trouble people get into when they go to the command line like we had to years ago. At this point I'd run the Live CD and create a new partition to back up all my user data. Then I'd do a clean install.

---

### Post by KarasuTengu on 2010-07-06
The card is a BFG NVIDIA Geforce 7800 GS AGP.  I have tried using the hardware drivers preference as well as the latest NVIDIA release.

---

### Post by warfacegod on 2010-07-06
As a whole this sounds like your having a driver issue. Try using one of the other drivers in Hardware Drivers if there are any.

> but there are some small pixel issues (random pixels are red or green).

This, specifically sounds like your monitor is getting "dead pixels". LCD's do that as they age. Try lightly running your finger over one to see if it goes away. If it does, you have two options.

.01 Replace the screen. (hassle)

.02 Buy a new monitor.

---

### Post by cascade9 on 2010-07-06
> **KarasuTengu said:**
> With a live cd the display looks fine compared to the screenshot I posted, but there are some small pixel issues (random pixels are red or green).

This problem started when I first upgraded to the latest 9.10 kernel, then upgraded to ubuntu 10.04.  I had to reinstall the drivers for my video card, and then after the restart for the driver refresh, everything went bad.

Sounds like the card is artifacting, which is a sign that it is going to the great pile of video cards in the sky sooner or later. 

Edit- if it was just under the nvidia proprietary drivers, then I migth guess ti was as driver issue..but under a ubuntu liveCD as well, thats a bad card. Unless its dead pixels like warfacegod posted, but I doubt it. 

I doubt that its a linux issue. If its not just the card getting old, then I would guess you've had a bit of long term damage from the dodgy nVidia drivers that were around for a while.....

---

