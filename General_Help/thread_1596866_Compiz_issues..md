---
title: "Compiz issues."
date: 2010-10-14
forum: General Help
---

### Post by Defib on 2010-10-14
Whenever I try to change desktop effects to anything other than none, a window appears saying 'Searching for driver' then the screen flashes and it says effects could not be enabled. 

Here's the output from System Testing Compiz test:


Gathering information about your system... Distribution: Ubuntu 10.10 Desktop environment: GNOME Graphics chip: ATI Technologies Inc M96 [Mobility Radeon HD 4650] Driver in use: fglrx Rendering method: None Checking if it's possible to run Compiz on your system... [SKIP] Checking for hardware/setup problems... [SKIP] At least one check had to be skipped: Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

What else do you want posted here to help?

---

### Post by 3Miro on 2010-10-14
Something is wrong with your video driver. Try to reinstall it.

System -> Admin -> Hardware Drivers, remove the driver, reboot, add the driver, reboot.

For an ATI card you can try the default driver as well (i.e. no driver), it should allow good desktop effects (for me the default worked better than the one proprietary one).

---

### Post by Defib on 2010-10-14
I tried both of those suggestions and it still says Desktop Effects could not be enabled.

---

