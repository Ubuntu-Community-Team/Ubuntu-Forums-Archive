---
title: "This Looks Easy on Linux - 3d Acceleration"
date: 2010-06-20
forum: General Help
---

### Post by Quarkrad on 2010-06-20
I have a nvidia Geforce 8500 on my 10.04 system - the driver I'm using is:  NVIDIA accelerated graphics driver (version current) [Recommended]  When I look at System/Preferences/Monitors I am asked if I want to use the vendor's graphics tool and up pops the NVIDIA X Server Settings window.  How do I enable 3D acceleration?

---

### Post by NCLI on 2010-06-20
It should be enabled automatically after you install the nVidia driver.

To find out whether 3D acceleration is working, enter in a terminal:

```
glxinfo | grep rendering
```

If 3D acceleration is working, the result will be:

```
direct rendering: Yes
```

---

### Post by Quarkrad on 2010-06-21
I have 3D - thanks you.

---

