---
title: "3D Hardware Acceleration"
date: 2010-11-08
forum: General Help
---

### Post by LloydSev on 2010-11-08
I have an ATI Radeon HD 3650.
Running Ubuntu 10.10 (Upgraded from 10.04)

My issue is pretty straight forward.
I loaded the default flgrx driver from the "Hardware Drivers" app. With these drivers the system is noticably slow, and not fun browsing the web as I can't hardly scroll in Firefox or Chrome.

So I updated to the newest drivers from the ATI website. Same results.

Third step was to add "http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu" to my respositories as it changed a few Xorg files and upgraded the ATI driver as well, yet still no dice.

I've used Ubuntu before with an nVidia card so I know how the OS is supposed to act. I've had friends who have experienced this issue when using an ATI card before, a generally poor taste left from the general operation of the system.

Is there anything I can do short of going out and buying a new video card?

Thanks

---

### Post by LloydSev on 2010-11-08
I'm dyin' .... lol

glxgears only gives me 120 FPS .... which is great for gears, horrible for anything larger than 640x480 lol.

---

### Post by 3Miro on 2010-11-08
I had an ATI 4850 and I had all of those issues. I did end up getting a new video card. Supposedly there is a new FOSS driver for the newest ATI cards (5xxx and up), but it is not in Ubuntu yet. Many people get better performance with the default ATI driver, it is not good for 3D games and such, but for regular use of FireFox and such it is probably better.

---

### Post by LloydSev on 2010-11-08
> **3Miro said:**
> I had an ATI 4850 and I had all of those issues. I did end up getting a new video card. Supposedly there is a new FOSS driver for the newest ATI cards (5xxx and up), but it is not in Ubuntu yet. Many people get better performance with the default ATI driver, it is not good for 3D games and such, but for regular use of FireFox and such it is probably better.

I've read about people trying to revert back and when removing the flgrx driver it ends up breaking stuff ... is that normal or is it simple to revert back?

---

### Post by dcstar on 2010-11-09
> **LloydSev said:**
> I have an ATI Radeon HD 3650.
Running Ubuntu 10.10 (Upgraded from 10.04)
..........
Is there anything I can do short of going out and buying a new video card?


Never "upgrade", always do fresh installs of new versions.

Boot off the 10.10 CD and see if the video works better, if so then your upgraded system probably has junk from previous versions causing the problem.

---

### Post by mastablasta on 2010-11-09
> **dcstar said:**
> Never "upgrade", always do fresh installs of new versions.
 
Boot off the 10.10 CD and see if the video works better, if so then your upgraded system probably has junk from previous versions causing the problem.
 
 
he could upgrade but would have to remove the driver completelly before upgrading the system. and then install a new driver.

---

### Post by LloydSev on 2010-11-11
> **mastablasta said:**
> he could upgrade but would have to remove the driver completelly before upgrading the system. and then install a new driver.

To be fair, my system was a fresh install of 10.04, immediately upgraded to 10.10 before I did any system modifications.

---

### Post by LloydSev on 2010-11-11
> **3Miro said:**
> I had an ATI 4850 and I had all of those issues. I did end up getting a new video card. Supposedly there is a new FOSS driver for the newest ATI cards (5xxx and up), but it is not in Ubuntu yet. Many people get better performance with the default ATI driver, it is not good for 3D games and such, but for regular use of FireFox and such it is probably better.

I removed the fglrx driver and reverted back to the original FOSS driver by going to "Additional Drivers" under Administration, then deselecting the proprietary driver there. After a reboot I can now watch videos, use web browsers, other normal "2D" applications with good performance.

glxgears now reports 60FPS, but so long as my system is usable I can deal with not being able to play any games until I upgrade my system I suppose ...

This has definitely spoiled my opinion of AMD/ATI completely in regards to graphics. I was heavily an nVidia fan before, going solely for the ATI card because it was the only AGP solution available quickly at my local stores, assuming that my bias was the sole reason for my bad opinions. I will think long and hard before I ever buy another AMD graphics solution.

---

