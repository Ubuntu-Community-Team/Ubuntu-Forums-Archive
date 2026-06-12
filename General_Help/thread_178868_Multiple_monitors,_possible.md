---
title: "Multiple monitors, possible?"
date: 2006-05-18
forum: General Help
---

### Post by Nasso on 2006-05-18
Hi all.
I want some of that multimonitor love! :) Have you ever seen anyone in a move have like 10 monitors and though "OMG that is friccin sweeet"?

Is it possible to have one CRT, two LCD and one TV attatched to a computer, in ubuntu, ofcourse. I want to extend my desktop on all monitors and clone one of the monitors on my tv, for displaying movies. (does that work? will be wierd with fullscreen and all that)

I have an radeon 9500 AGP gfx-card right now. It got one VGA, one DVI and one svhs-connector. There is not enough connections. Is it possible to buy a pci-gfx with a dvi-connector on it or one with a VGA-connector and get a vga-dvi-converter for my radeon 9500.

is this possible with fglrx? Is it possible at all?

---

### Post by gerbman on 2006-05-18
Dual screen is definitely possible (I'm currently running a 19" LCD and 30" TV on my 9500 Pro). I don't think you can do more than 2 screens. Have you installed the fglrx drivers for your 9500 card? If you have, then run```
sudo fglrxconfig
``` to set up dual screen support. It will probably take some fiddling around with to get it working, so first back up your xorg.conf file (the file that tells the system how to set the displays up, among other things):```
cp /etc/X11/xorg.conf ~/xorg.conf_backup
```Run fglrxconfig and then hit CTRL+ALT+BACKSPACE to restart X. If the system won't load, you need to restore your xorg.conf file. Hit CTRL+ALT+F1 to log into a terminal, and do```
sudo cp ~/xorg.conf_backup /etc/X11/xorg.conf
```to restore your original xorg.conf file. Then restart your system and try again. You can accept default values in fglrxconfig by hitting enter. The only thing you need to change is the dual screen section. It took me a couple tries to get what I wanted.

---

### Post by Nasso on 2006-05-19
Dual screen is no problem, there is a gui and plenty of guides out there. I want three screen with one extended desktop on one AGP-card and one PCI-card, that is the problem :)

Thanks anyway though!

---

