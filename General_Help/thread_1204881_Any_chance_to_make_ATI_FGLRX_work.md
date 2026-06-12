---
title: "Any chance to make ATI FGLRX work?"
date: 2009-07-05
forum: General Help
---

### Post by johann_p on 2009-07-05
I am running my Lenovo T500 with the BIOS set to always use the built-in ATI and not the Intel graphics subsystem.
lspci shows:
```

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

```The Hardware Drivers menu shows that there is a proprietary driver available: "ATI/AMD proprietary FGLRX graphics driver" and I would love to use it BUT:

Using the proprietary driver will make it impossible to view DVB-T using kaffeine as it will invariably crash. Since I want to use my laptop as a TV I therefore cannot use the proprietary driver (it seems this is because the xine engine crashes but the gstreamer engine cannot be used for DVB-T)
On the other hand, not using it sucks with regard to using 3D like GoogleEarth and other programs.

Is there any chance to make this work as it should?

---

