---
title: "X goes blank every time"
date: 2005-03-03
forum: General Help
---

### Post by plichocki on 2005-03-03
Hi,

I can't configure my X to work with my monitor. I have a Hyundai Delux Scan 15G [30-64khz / 50-130hz - according to spec]. So I have edited /etc/X11/XF86Config-4 with proper info in device section, but every time I start X window monitor momentally goes blank. I know it's not the fault of the graphic card, because I have succesfuly configured ubuntu X window to work with my SONY CPD-110EST.
But unfortunatelly I've got two computers and I need two monitors, so I need to configure the Huyndai with ubuntu.

---------------------------------
Section "Monitor"
Identifier "DeluxScan15G"
HorizSync 30-64
VertRefresh 50-130
Option "DPMS" //what's that?
EndSection
---------------------------------

I have tried many various combinations and still can't make it works. What else i can do?
thanks in advance, etc...

---

