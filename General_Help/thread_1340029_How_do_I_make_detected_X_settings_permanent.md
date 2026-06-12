---
title: "How do I make detected X settings permanent?"
date: 2009-11-28
forum: General Help
---

### Post by Listerofsmeg01 on 2009-11-28
Hi guys, newbie here.
 
I have MythBuntu running on a Revo for a TV front end. This works great.
 
The problem is that I have to have both the TV and amp on when the PC boots, otherwise I get no graphical interface. I am assuming something (HAL?) detects the available refresh modes on boot for X to use.
 
How can I find these and make them permanent, so that I can boot the box even with everything else off, and still get an interface when I turn the TV on.
 
Many thanks,
Lister

---

### Post by hirnwurscht on 2009-11-28
Hi Listerofsmeg01,

i assume you have an nvidia-card installed.

see [http://mythtv.org/wiki/Running_MythTV_Dual_Headed#PIP_Display_.28One_X_Server.2C_One_display.2C_Dual_head_video_card_with_a_desktop_on_each.29]("http://mythtv.org/wiki/Running_MythTV_Dual_Headed#PIP_Display_.28One_X_Server.2C_One_display.2C_Dual_head_video_card_with_a_desktop_on_each.29")

```
       Option          "ConnectedMonitor"      "CRT-0,DFP-0" #Force the connected monitor since only one can be active at a time
        Option          "UseDisplayDevice"      "CRT-0"

```

change CRT-0 and/or DFP-0 to what nvidia-settings finds if both displays are on.

hope that helps.

---

### Post by Listerofsmeg01 on 2009-11-29
Many thanks for your reply. It put me on the right track.
Those lines forced it to use the correct output port, so I was getting an image now, but it was the wrong resolution.
 
For anyone else with this problem, the issue seems to be that X (or at least the Nvidia driver) checks any mode that you request against the EDID data queried from the monitor. If the monitor is not connected, then no EDID is available, so the mode fails to validate and you get a fallback mode instead (640x480 in my case).
 
There are various X settings you can specify to ignore such things, but after faffing about for a bit I was getting nowhere.
 
In the end I just used the nvidia-settings util to write the EDID data to a file ("Aquire EDID"), and then told X to use this as a custom EDID with:
 
Option "CustomEDID" "DFP-0:/path/to/some/edid.file"
 
Sorted! :D

---

