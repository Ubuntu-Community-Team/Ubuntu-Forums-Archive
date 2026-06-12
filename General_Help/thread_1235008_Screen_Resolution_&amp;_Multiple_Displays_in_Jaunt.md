---
title: "Screen Resolution &amp; Multiple Displays in Jaunty"
date: 2009-08-08
forum: General Help
---

### Post by CJBishop on 2009-08-08
Let me preface by saying I'm completely new to linux, but I hope I've done enoug research to make this post helpful.

I'm running ubunto 9.04 Jaunty on a Dell Latitude D420.  Intel graphics card, so that's probably the root of my problems.  I just connected it to an HDTV, was able to set resolution no problem... But now that I'm disconnected from the TV, I can't set it back to its normal resolution (1280x800).  

My xorg.conf file in its entirety is this:
```

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```It seems suspiciously empty to me...  Any suggestions on how I can get back to 1280x800?

---

### Post by CJBishop on 2009-08-08
I worked it out...  I have Compizconfig installed, I just needed to go to the 'general settings' tab, it changed the output line to 1024x768+0+0, I changed it back to 1280x800+0+0, and was then able to set my resolution through System>Preferences>Display.  Hope this can help anyone else with similar problems.
:D

---

