---
title: "Catalyst 10.7 video driver issues"
date: 2010-08-16
forum: General Help
---

### Post by ThomasTheTan on 2010-08-16
Hi-

I recently upgraded to 10.04 64 bit, and my gpu is an ati HD 5770.

I wanted to install the proprietary drivers, and I read in various locations that the newest drivers on ati's site (catalyst 10.7) worked in 10.04 with the 5770 and that 10.7 was better to install than the drivers that can be obtained through System -> Administration -> Hardware Drivers.

So I followed the steps found [here]("http://www.overclock.net/linux-unix/509761-how-linux-ati-driver-installation.html") to install the drivers.

Problem is, upon reboot, everything is very choppy, and I still can't turn on compiz.  When I run fglrxinfo (as recommended on that site), I get the following error message:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18
```I've tried uninstalling and reinstalling the drivers numerous times to no avail.

Any suggestions would be met with a lot of smiles!

---

### Post by ThomasTheTan on 2010-08-16
Hi-

I recently upgraded to 10.04 64 bit, and my gpu is an ati HD 5770.

I wanted to install the proprietary drivers, and I read in various locations that the newest drivers on ati's site (catalyst 10.7) worked in 10.04 with the 5770 and that 10.7 was better to install than the drivers that can be obtained through System -> Administration -> Hardware Drivers.

So I followed the steps found [here]("http://www.overclock.net/linux-unix/509761-how-linux-ati-driver-installation.html") to install the drivers.

Problem is, upon reboot, everything is very choppy, and I still can't turn on compiz.  When I run fglrxinfo (as recommended on that site), I get the following error message:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18
```I've tried uninstalling and reinstalling the drivers numerous times to no avail.

Any suggestions would be met with a lot of smiles!

---

### Post by K.Mandla on 2010-08-16
Similar threads merged. :)

---

