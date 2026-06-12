---
title: "visual effects"
date: 2009-11-05
forum: General Help
---

### Post by nav9306 on 2009-11-05
hi
i recently installed ubuntu 9.04
and i likd it......but i cannot enable the visual effects which is really sad
wheneva i try to enable it  simply says "cannot enable visual effects" after hesitating for a few seconds
 my comp is an intel p4 1.7GHz
512MB RAM
64 MB internal graphics by intel
will it be possible for me to use the compiz effects like cube etc
please help me
will be thankful to any help provided

---

### Post by Giblet5 on 2009-11-05
Enabling desktop effects (compiz or KDE) requires a graphics processor with OpenGL and compositing support.

There is a reason why people are willing to pay more for a non-basic graphics system: it does more.

The fancy graphics aren't that big of a deal though. The ability to do a LOT of stuff, free, is a decent consolation prize.

---

### Post by ibokozan on 2009-11-05
it may be your video driver is not supported by ubuntu and dont work, check it system - hardware as i remember :)

---

### Post by taylor1234 on 2009-11-05
sudo apt-get install compizconfig-settings-manager

try typing that into the terminal. after it downloads look in the 
system>preferences(or admin?)>comprizconfig-settings manager.
I think thats what i did but i may have downloaded something else too.??
from there you can turn on the cube and other effects.

---

### Post by nav9306 on 2009-11-06
i installed the compiz settings manager but cannot use them though

---

### Post by P4man on 2009-11-06
post the output of
```
lspci
```

but it will probably only serve as a confirmation of the fact you have an onboard video  unable to handle compiz.

---

### Post by nav9306 on 2009-11-06
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)

---

### Post by nav9306 on 2009-11-07
next problem
i cannot connect my nokia 5130 in ubuntu......is there any special program that i have to install?

---

### Post by Jr.Muffin on 2009-11-07
You will need to update Ubuntu to enable your visual effects. When Ubuntu 9.04 came out, the graphics card you are using was blacklisted. They removed it in one of the updates.

---

