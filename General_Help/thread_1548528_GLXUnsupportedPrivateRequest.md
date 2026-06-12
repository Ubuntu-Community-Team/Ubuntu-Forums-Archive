---
title: "GLXUnsupportedPrivateRequest"
date: 2010-08-08
forum: General Help
---

### Post by dieter-erich on 2010-08-08
Hi,
   the molecular graphics software UCSF Chimera runs perfectly well on both a PC and an Asus EEE  Nettop. There is no problem with the graphics. However, when running it remotely from the EEE over ssh -X user@.... I get the message:

  X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  725
  Current serial number in output stream:  726

compiz-check shows:
 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

I suspect that it is a problem of the ssh or DISPLAY settings

Thanks for hints, D-E

---

### Post by bodhi.zazen on 2010-08-08
Moved to general help as the tips and tutorials section is not for support questions.

---

### Post by dieter-erich on 2010-12-13
Hi, thanks for moving my post to the correct forum. However, I do not find it any more under my threads. How can I find it (and possible answers)?
D-E

---

