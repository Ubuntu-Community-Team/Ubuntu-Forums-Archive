---
title: "HDMI with fglrx (4650)"
date: 2009-08-24
forum: General Help
---

### Post by evol262 on 2009-08-24
For the life of me, I cannot seem to get straight HDMI working with fglrx on a 4650.  The system has an onboard 3200, which works as expected, but when I switch to the 4650 (clean install or not), I get no output from HDMI after installing fglrx.  As soon as X attempts to start, it starts (and fails) to initialize an HDMI connection, then drops me back.  Failsafe X hangs the system once fglrx is installed (currently disabled).

Xorg.0.log indicates that it can't find a screen, and no aticonfig incantation I've tried will get it to initialize (--fore-monitor=tdmsX).  The HDMI connector is the only input I've got, and VTs work normally.

It works through a DVI->HDMI adapter, sort of (amdcccle then cannot detect that it's connected to a television, so I can't change the overscan to get it to fill the screen, and I obviously have no audio that way).  Straight HDMI works if I disable RandR, but the 1080p is not an option (if I specify the modeline myself, it'll switch, but there's corruption on the right half of the screen in anything above 1440).

Does anybody have HDMI working with a 4650 and fglrx?  I'm ready to try openSUSE or Arch just to see if I can get it working, but staying with Ubuntu would be the ideal.

---

