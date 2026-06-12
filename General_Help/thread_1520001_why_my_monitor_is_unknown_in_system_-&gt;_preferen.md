---
title: "why my monitor is unknown in: system -&gt; preferences -&gt; monitor?"
date: 2010-06-29
forum: General Help
---

### Post by mafeusek on 2010-06-29
Hallo Everyone!

I wonder why is my monitor type not recognized?

pressing "detect monitors" button in system->preferences->monitors does not do the effect.

my /etc/X11/xorg.conf tells (which is correct):

Section "Monitor"
    #DisplaySize      300   230    # mm
    Identifier   "Monitor0"
    VendorName   "SAM"
    ModelName    "570B/580B TFT"
    HorizSync    30.0 - 61.0
    VertRefresh  50.0 - 75.0
    Option        "DPMS"
EndSection

I am running ubuntu 10.04.

$ lspci
...
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 04)
...

Have You got an idea what might be the reason?

best regards,
Pawel

---

