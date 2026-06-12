---
title: "Old monitor, new ATI Card"
date: 2009-10-30
forum: General Help
---

### Post by FlyinRedneck on 2009-10-30
Hello all! I seem to be having a peculiar problem with my monitor and card in Ubuntu 9.10 and FGLRX drivers. Everything works except fot the fact that the driver is displaying a resolution and frequency range that are out of the monitors range. I have already specified the refresh rate and other similar information in my Xorg.conf and it is registering the values. I have tried everything else I have seen on the internet, but for some reason nothing really works. Can someone put me in the right direction in dumbing X down to my monitor so I am not stuck without 3d acceleration?

Here is my xorg.conf from memory (not all to accurate)

```
Section   Device
   Identifier "Radeon HD 2600 PRO"
   Driver   "FGLRX"
EndSection

Section   Screen
   Identifier   "Default Screen"
EndSection

Section   Monitor
   Identifier   "Default Monitor"
   VertRefresh   60-120
   HorizFreq   30- *i forgot the number*
   Option   "(refresh default or something like that)"   60
EndSection
```

---

### Post by lilbill on 2009-10-30
Have you tried changing it in GNOME?  Go to System->Preferences->Display  and you should be able to edit the refresh there.

---

