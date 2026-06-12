---
title: "Struggling to find what infomation the X server is using"
date: 2009-07-15
forum: General Help
---

### Post by Felt on 2009-07-15
Hello,

I understand that the new X server is using some form of automatic configuration if the the configuration has not been done in the [FONT=Courier New]/etc/X11/xorg.conf. [FONT=Verdana]

My xorg.conf looks like this:

[/FONT][/FONT]```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```I wish to know what video drivers Xorg is choosing (or what would be lovely, is to have Xorg dump a proper xorg.conf file based on what it has chosen!). I read that X keeps all it's configuration data in memory, so I didn't even bother looking for other conf files. Is there a utility to get at this information? 

Thanks for reading.

---

### Post by Felt on 2009-07-15
Sorry, I should really check log files more often!

All the information is in /var/log/Xorg.0.log :)

Silly me.

SOLVED.

---

