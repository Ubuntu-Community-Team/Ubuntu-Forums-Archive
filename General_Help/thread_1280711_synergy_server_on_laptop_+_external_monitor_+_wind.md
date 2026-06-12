---
title: "synergy server on laptop + external monitor + windows client on external monitor"
date: 2009-10-02
forum: General Help
---

### Post by hearmemeow on 2009-10-02
My laptop (Latitude D820) is running Ubuntu 9.04, resolution 1280x800
An external monitor is attached to the laptop, resolution 1680x1050
My desktop is running Windows XP

I have the Synergy server installed on the laptop and the client on the desktop

Synergy is working correctly except for one annoying problem: it thinks my external monitor resolution is that of the laptop, so that moving the mouse to the right of pixel 1280 sends it to the Windows screen

--

I would be happiest if I could run the laptop with the external monitor on and laptop screen disabled but am open to either scenario.

So far I've had the same problem when I enable or disable the laptop screen in the control panel.

--

Previously I ran Synergy with server from Windows and Ubuntu client - same issue.

---

### Post by jwmuelle on 2009-11-10
are you still trying to figure this out?

you need to (re)start synergy after changing the screen sizes (physical or virtual).  

If synergy starts before your external monitor is configured (either via normal startup, or manually via the display app, or via script by xrandr in a startup sequence someplace) you have to re-start synergy to pick up the new screen size(s).  If you have everything starting automatically, find the place where synergy is starting up and add a "sleep 5"  (or 10 or whatever you need, without the quotes) to the script prior to the synergy(s/c) command to give the displays adequate time to configure before synergy starts.

jw

---

