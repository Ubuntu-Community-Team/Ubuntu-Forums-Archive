---
title: "Black screen on login with compiz (Intel 845 integrated graphics)"
date: 2009-11-01
forum: General Help
---

### Post by flipper9 on 2009-11-01
Any updates or tweaks I can make to get the following to work???

Distribution: Ubuntu 9.10 (Karmic) Release with all updates installed via update-manager
Desktop: GNOME
Graphics Chip: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
Driver in use: intel
Rendering method: AIGLX

texture_from_pixmap: OK
non power of two support: OK
composite extension: OK
FBConfig: OK
hardware/setup problems: WARN=blacklisted

Warning: PCI ID 8086:2562 detected
===========
Tried to enable compiz, couldn't. Installed the xorg-edgers drivers, then compiz let me enable desktop normal effects.  System hard-froze.  Tried rebooting, cet bootup ubuntu logo, then desktop loads with the circular mouse icon, then screen goes black.

Any ideas (other than disabling compiz entirely?) on how to get this to work?

---

### Post by Ervin Burkus on 2010-01-02
[B]The same here... Still...
Ubuntu Black screen on login with compiz (Intel 845 integrated graphics)[/B] 			
 			 			 		   		 		 		Clear Ubuntu 9.10, Updated, Intel 845, Blacklist ignored, tried several Intel drivers...
Was trying 2 days to solve the problem, but nothing works.

Any ideas (other than disabling compiz entirely?) on how to get this to work?

---

### Post by falconindy on 2010-01-02
Add the following to your kernel options in GRUB:
```
i915.modeset=1
```
This will enable KMS, which is something that will be required of Intel cards (via the driver) going forward.

---

