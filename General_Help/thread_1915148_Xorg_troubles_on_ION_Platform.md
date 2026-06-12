---
title: "Xorg troubles on ION Platform"
date: 2012-01-25
forum: General Help
---

### Post by vz360 on 2012-01-25
Hi,

I'm sorry if I'm posting this in the wrong forum - I tried locating similiar threads but the search function always timed out.

I'm in the process of setting up Ubuntu on my HTPC and I can't get the display configuration to work.

My setup:
Zotac ION Mainboard with Atom N330 CPU, 2GB RAM
A 15" flat-panel display connected to the DVI-Port
A Samsung SPB-A600B Beamer connected to the HDMI-Port

Here's what I would like to achieve:
- When I boot up the computer only the LCD should be used to display Gnome or XBMC.
- Being able to switch to betweend the Beamer and the LCD using a script (I'm using disper to do this)

The problem is, that as long as the beamer is attached during boot-up (even if it's unplugged) the LCD is disabled and the X-screen moves to the beamer as soon as I log in.
I tried to disable the beamer by setting the Ignore-Option in the xorg.conf but it had no effect at all.

Currently I'm using ubuntu without an xorg.conf and just let the auto-detection do it's magic (which I suspect is responsible for automatically switching to the beamer).

I'm using the latest version of ubuntu, installed all updates and the latest drivers.


Please share your wisdom with me ;-)

---

