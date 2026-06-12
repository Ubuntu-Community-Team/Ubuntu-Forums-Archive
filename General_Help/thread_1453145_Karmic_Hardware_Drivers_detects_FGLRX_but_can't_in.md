---
title: "Karmic Hardware Drivers detects FGLRX but can't install it"
date: 2010-04-12
forum: General Help
---

### Post by hangfire on 2010-04-12
I'm running Kubuntu 9.10. Moving my disk over from my old system, it detected the onboard ATi 4200 with one reconfig of X, and I can see video, run glxgears, etc.

Not one to leave well enough alone, I brought up Hardware Drivers (jockey-kde), give kdesudo my pw, wait for it to search for drivers, and it tells me I can install FGLRX. Great! 

I click _A_ctivate and (other than the button push visual), nothing happens. I restarted X, tried again, rebooted, tried again. I checked Xorg.0.log and it seems to be loading [ati, radeon, vesa, and fbdev]_drv.so each time, but no mention of fglrx.

I am aware that some older ATi hardware is not longer supported, but I purchased all this new hardware (see signature) after much research and seeing that it was well supported by Karmic out of the box. I cannot find any log files that indicate that jockey is even trying anything, let alone failing.

Any tips?

-HF

---

### Post by dcstar on 2010-04-13
> **hangfire said:**
> I'm running Kubuntu 9.10. Moving my disk over from my old system, it detected the onboard ATi 4200 with one reconfig of X, and I can see video, run glxgears, etc.
.........

Moving existing installs to different hardware is usually a disaster. So much is configured during the initial installation process that just allowing a reboot with different hardware is usually not good enough to make things work correctly.

Make a separate /home partition and then do a proper fresh install to get a system set up correctly with the hardware.

---

### Post by Untitled_No4 on 2010-04-13
While basically agreeing dcstar, I think you're experiencing a quite exotic bug in Jockey. Try loggin out and in again and run Jockey again. The top half of the window will list the driver and the bottom half will show the details. Click on the driver name on the top half, then click on the description on the bottom, back on the driver on the top and then Activate. Does it work now?

---

### Post by hangfire on 2010-04-13
> **Untitled_No4 said:**
> Click on the driver name on the top half, then click on the description on the bottom, back on the driver on the top and then Activate. Does it work now?

Thanks No 4, you nailed it!

I also agree with dcstar, I already have a separate /home that has been with my since I bought the disk, and its predecessors since 5.04.

I stuck this disk in with the 9.10 install CD at the ready, and never needed it. It is just temporary until 10.4LTS is released, my ultimate goal for this system.

-HF

---

