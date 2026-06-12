---
title: "Why this happens?"
date: 2009-12-04
forum: General Help
---

### Post by baskar007 on 2009-12-04
I had a problem with xorg on my ubuntu 9.10 fresh install.  Xorg process always takes 100% cpu usage, and ubuntu hangs completly.(i cant enable Desktop effects)

I had tried to reinstall video driver for my Graphic-card but no use.

lsPCI output:
```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
**00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

i have installed 
xserver-xorg-video-intel  (Is this is correct drive for i945 card ?)
and i tried to install xf86-video-intel but package not found on apt 

any solution?

---

### Post by khelben1979 on 2009-12-04
Have you tried switching different Linux kernels to see if anything works better? (search in [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_package_manager") for them)

---

### Post by baskar007 on 2009-12-04
Thank you for your help,
i already passed those stages, currently i have a problem in turn on kms.

i get this error
```
ERROR module i915 does not exist in /proc/modules
```

when running this codes for turn on kms
```

sudo rmod i915

```

any ideas??

---

### Post by khelben1979 on 2009-12-04
Maybe the module isn't part of the Ubuntu kernel? Or you can try with insmod or modprobe instead to see if it helps. Use the man pages if you're uncertain of how to use them.

---

