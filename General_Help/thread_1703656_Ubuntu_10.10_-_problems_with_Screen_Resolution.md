---
title: "Ubuntu 10.10 - problems with Screen Resolution"
date: 2011-03-09
forum: General Help
---

### Post by Limosos on 2011-03-09
Hi,

I'm sorry to plague you all with this n00b question, but I've spent hours trying to figure this out with no joy.

I've installed Ubuntu 10.10 on my laptop, only to find I only have low resolution problems. I've looked at various forum threads to try and fix this and I've had no joy. 

I got my system info and it's:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

All the tutorials tell me to try and use xorg, with commands like: Edit /etc/X11/xorg.conf

but I always get a response of 

 Command 'edit' from package 'mime-support' (main)
Edit: command not found

All tutorials seem to take this route and i'm baffled - and a bit tired of everything being huge!

Any help would be gratefully received.

Thanks :D

---

### Post by turtle153 on 2011-03-09
edit isn't a command. Use```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by lithopsian on 2011-03-09
This is Linux, baby :)  Try "leafpad /etc/X11/xorg.conf" (or gedit) or edit it from your favourite file manager.  There actually is a program called just edit in the package mime-support but I don't think you want to install that.

Of course you have to know what you want to edit it to ;)

---

### Post by Limosos on 2011-03-09
The gedit command brought up a series of values:

Section "Monitor"
Identifier "Monitor1"
VendorName "DEL"
ModelName "DELL P1110"
HorizSync 29-121
VertRefresh 50-180
EndSection

I think I added these as part of a tutorial earlier though! I assume I need to change the values for my laptop's monitor info?

---

