---
title: "GLX Unsupported Private Request"
date: 2010-12-14
forum: General Help
---

### Post by dieter-erich on 2010-12-14
**GLXUnsupportedPrivateRequest** 
Hi,
the molecular graphics software UCSF Chimera runs perfectly well on both a PC and an Asus EEE Nettop. There is no problem with the graphics. However, when running it remotely from the EEE over ssh -X user@.... I get the message:
 
X Error of failed request: GLXUnsupportedPrivateRequest
Major opcode of failed request: 153 (GLX)
Minor opcode of failed request: 16 (X_GLXVendorPrivate)
Serial number of failed request: 725
Current serial number in output stream: 726
 
compiz-check shows:
Distribution: Ubuntu 10.04
Desktop environment: GNOME
Graphics chip: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
Driver in use: intel
Rendering method: AIGLX
 
I suspect that it is a problem of the ssh or DISPLAY settings
 
Thanks for hints, D-E
 
P.S. sorry I already posted. But according to an answer of a maintainer it was moved to General Help where I was unable to find it, so I posted again.

---

### Post by dieter-erich on 2011-03-04
Solved by replacing the nvidia drivers with the noveau drivers!

---

