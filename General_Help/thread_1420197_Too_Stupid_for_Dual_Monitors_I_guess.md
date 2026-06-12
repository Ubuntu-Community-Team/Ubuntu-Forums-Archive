---
title: "Too Stupid for Dual Monitors I guess"
date: 2010-03-02
forum: General Help
---

### Post by ronnielsen1 on 2010-03-02
Ok, I was playing around with trying to get dual monitors setup on my box and I came to the conclusion that nvidia-settings in the menu was junk and I'm not even sure why it's in there since it doesn't work. gksudo nvidia-settings didn't work too hot either. I tried gksudo gedit /etc/X11/xorg.conf many times with various results, none satisfying.

My relevant part of lspci -vv is


01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 248 (1250ns min, 250ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Region 2: Memory at d8000000 (32-bit, prefetchable) [size=512K]
    [virtual] Expansion ROM at d8080000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb, rivafb

My primary monitor is a NEC LCD1712 flat screen and the 2nd monitor is a Proview PX-5605


NEC LCD1712:

[LIST]
[*]1,280 x 1,024 maximum resolution, 0.264 mm dot pitch
[*]140-degree horizontal and 120-degree vertical viewing angles
[*]250 cd/m2 of brightness, 450:1 contrast ratio
[*]16 ms response time for smooth motion video
[/LIST]
Proview PX-5605:
[B]
Product has been discontinued or not in stock[/B]

Um yeah I know, it's an old monitor built in 2001

If anyone knows how I can edit xorg.conf to reflect this, I would appreciate it. Thanks.:D

---

### Post by overdrank on 2010-03-02
Hi and I have a similar nvidia graphics card GeForce4 Ti 4800. I have used dual monitors in the past with no issues. 
What are you having issues with? Resolution, separate (X) screens?
I am using the system now for testing Lucid Lynx now but maybe I can help with 9.10 Karmic Koala :)

---

### Post by ronnielsen1 on 2010-03-02
> I am using the system now for testing Lucid Lynx now but maybe I can help with 9.10 Karmic Koala
That would be great. I did have Lucid on it but I couldn't get the drivers going so I went back to 9.10. I try to adjust the settings but I was getting too high of a resolution on the old monitor and it was like one big window. I'd prefer to use the flatscreen as a primary and the old one as a secondary but I'm not entirely sure how to do it.

---

