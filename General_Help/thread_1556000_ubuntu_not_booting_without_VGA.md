---
title: "ubuntu not booting without VGA"
date: 2010-08-18
forum: General Help
---

### Post by noobatron on 2010-08-18
hi guys, i have an old laptop with ubuntu fully installed and funtional the way i like it, this is a dedicated boinc machine which has had it's internal screen ripped off (by me upon obsolescence as a laptop, stops overheating with boinc when modified) and under normal cirumstances (non maintenance) has only power and ethernet connected

i moved from windows to ubuntu 10.04 x32 recently and i noticed that the computer doesn't pick up vnc requests nor start boinc (i can tell because hte processor heatsink doesn't heat up when i touch it) after booting up if there is no VGA connected on boot, but if i connect vga, boot and then remove, everything is perfect. (it used to boot into windows just fine and begin VNC and boinc all normal, it was insensitive to whether the VGA was there or not on boot)

when i later attempt to connect a VGA after booting without one connected, the screen merely sleeps and does nothing.

so my question is, is there anyway to make ubuntu boot thinking that a screen is connected? VGA terminators are not easily found where i live and i'd like to avoid making one if a software solution exists (which it probably does)

thank you in advance.

---

### Post by dcstar on 2010-08-19
> **noobatron said:**
> 
.........
so my question is, is there anyway to make ubuntu boot thinking that a screen is connected? VGA terminators are not easily found where i live and i'd like to avoid making one if a software solution exists (which it probably does)

thank you in advance.

Create a custom /etc/X11/xorg.conf file so the system does not try to auto-detect hardware that obviously is not there.

---

### Post by noobatron on 2010-08-23
i tried having a look at how to do this, looks extremely complex, anyone have any guidelines/pointers as to how to proceed or what my objective should be? i could probably sort out the rest, but dunno.

thanks.

---

