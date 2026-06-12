---
title: "cant change my resolution in 10.04"
date: 2010-07-27
forum: General Help
---

### Post by Virtueofselfishness on 2010-07-27
when i try to change my resolution in 10.04 i get a msg saying

"it appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

---

### Post by clhsharky on 2010-07-27
Virtueofselfishness

Hardware Information
```
lspci | grep VGA
```

Sharky

---

### Post by Virtueofselfishness on 2010-07-27
> **clhsharky said:**
> Virtueofselfishness

Hardware Information
```
lspci | grep VGA
```Sharky

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
01:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by Virtueofselfishness on 2010-07-28
Bump!

---

### Post by jerenept on 2010-07-28
Use System>Administration>NVIDIA X Server Settings.

Click "X Server Display Configuration."

Configure your display as you see fit.

---

### Post by lizzibet on 2010-07-28
in oter words if your nvidia-settings icon doesn't appear ib the system menu then open a terminal and type gksudo nvidia-settings to adjust them.

---

