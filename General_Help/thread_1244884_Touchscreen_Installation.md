---
title: "Touchscreen Installation"
date: 2009-08-19
forum: General Help
---

### Post by awd-s on 2009-08-19
This report is for those persons contemplating the use of a touchscreen and to help expand the database of successful installations.

Touchscreen installation was easy on Ubuntu release 8.10 (intrepid), kernel 2.6.27-14generic, GNOME 2.24.1. 

I attached a Planar PT1701MX monitor with capacitive touchscreen to the USB port of an early CompuLab Fit-PC. Command *lsusb* reported:

```
0eef:0001 D-Wav Scientific Co., Ltd. eGalax Touchscreen
```

I loaded the generic X.Org touchscreen driver from the repositories:

```
xserver-xorg-input-evtouch  Touchscreen Driver for X.Org/XFree86 Server
```

The Planar touchscreen worked immediately and only required calibrating by running the Touchscreen Calibration utility listed on the System-Administration menu after installation of the driver. Disconnecting the mouse seemed to smooth this process, preventing confusion with the touchscreen inputs.

The Fit-PC-Planar combination is running in a public place as a kiosk with FireFox enhanced with the R-kiosk add-on. Auto-login is enabled to the unprivileged public account, so no user intervention is required to start the system, which runs continuously. The equipment is locked in the pedestal below the touchscreen, inaccessible to users of the system.

Good luck with your touchscreen projects.

---

