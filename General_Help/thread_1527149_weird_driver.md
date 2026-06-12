---
title: "weird driver??"
date: 2010-07-08
forum: General Help
---

### Post by Johnny13811 on 2010-07-08
Hey, I'm running Ubuntu 9.10 on a Sony Vaio with an nVidia G210M graphics card. When I got to hardware drivers the recommended driver is nVidia accelerated graphics driver (version 185), however when I install in and reboot the system the screen flashes and eventually stops on but nothing shows up, but the music still plays as if it were working swimmingly. Sorry just wanted to use that word. Any ways back on track, so I have to use the vesa driver. Somehow I managed to install a driver called nVidia Riva/TNT/Geforce I have no idea what this is but it adds the AIGLX rendering method, I still can't run the visual effects because of the driver in use is vesa. I went to install the recommended nVidia driver (185) and once again it flashes like before that the music still plays. I switched to the vesa driver again to find that the nVidia Riva/TNT/Geforce driver was installed and activated again but this time there is no rendering method. I run ./compiz-check and this is what I get: 
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Device 0a74 (rev a2)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

does anyone have an idea on what this nVidia Riva/TNT/Geforce driver is and why my rendering method disappears and possibly getting visual effects to work. I'm new to Linux. All help is appreciated.

---

