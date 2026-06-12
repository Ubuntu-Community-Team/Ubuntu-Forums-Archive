---
title: "OpenGL And Desktop Effects are very slow"
date: 2009-09-21
forum: General Help
---

### Post by MegaLoler on 2009-09-21
I recently installed Ubuntu 9.04 on a g4 mac and the openGL was very slow with a blue background and weird colors and the desktop effects wouldn't work. Then I updated the kernel and that made things a little better.  The blue background was gone and open gl was a little faster.  Desktop effects work now but are extremly slow.  Extreme Tux Racer runs at about 1fps but the screen savers run at nice speeds.  I searched around the forums but couldn't find anything that worked.  When I do glxinfo | grep direct in terminal, it returns Yes.  Can anyone help please?

Edit:  I fixed a few things, the updated problems are that Tux Racer Runs Very Slow and When desktop effects are turned on, they are fast, but the graphics are glitchy. Like There are no title bars for windows and artifacts appear somtimes.

---

### Post by MegaLoler on 2009-09-21
I just added the defaultdepth 16 item to my xorg.conf file and the desktop effects work very well now!  But the screen was upside down and I had to change that back to normal.  Also the windows are messed up and they don't have title bars, and the desktop switcher doesn't work.  And Extreme Tux Racer is still very slow.

---

### Post by Tipped OuT on 2009-09-21
What is your graphics card?

---

### Post by MegaLoler on 2009-09-21
> **Tipped OuT said:**
> What is your graphics card?
Actually, I'm not 100% sure, but i think its ati nvidia (not sure how to spell it) or something like that.  Is there an easy way to check?
p.s. the desktop switcher does work, it was just disabled

Edit:  I ran sudo lspci |more and i got:

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200]
 (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 
81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) 
(rev 80)

---

