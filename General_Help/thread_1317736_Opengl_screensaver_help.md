---
title: "Opengl screensaver help"
date: 2009-11-07
forum: General Help
---

### Post by dragon84 on 2009-11-07
hi guys,
i have a fairly new installed ubuntu 9.10 installed on the system and i need help installing opengl screensavers into it. in version 9.04 ubuntu had some neat opengl screensavers installed but they were removed out of 9.10. well i found a site which has these screensavers i wanted at [http://rsxs.sourceforge.net/downloads](http://rsxs.sourceforge.net/downloads). i have no idea how to install them. 

i have:
- downloaded theSource tarball (rsxs-1.0.tar.gz)
- $ tar xzf rsxs-1.0.tar.gz[FONT=monospace]
 [/FONT]$ cd rsxs-1.0[FONT=monospace]
 [/FONT]$ ./configure

and get this message "configure: error: can't compile without OpenGL support".

does any users know how to solve this issue?

many thanks

---

### Post by RedSingularity on 2009-11-07
Are you running 64bit or 32bit?

---

### Post by dragon84 on 2009-11-07
32bit

---

### Post by RedSingularity on 2009-11-07
From that site you linked download the .rpm file.  

Make sure you have "alien" installed in the synaptic package manager.  

We will use alien to convert the RPM to a DEB that will install itself.

---

### Post by RedSingularity on 2009-11-07
1)  Save RPM to desktop
2)  In terminal do "cd ~/Desktop" without quotes
3)  In terminal do "sudo alien -k name-of-rpm-file.rpm" without quotes
4) This will create a DEB file that you can click and installs itself. :)

---

### Post by dragon84 on 2009-11-07
ok i have downloaded alien and it does not open. it also has a "?" as the icon

---

### Post by RedSingularity on 2009-11-07
> **dragon84 said:**
> ok i have downloaded alien and it does not open. it also has a "?" as the icon


You downloaded alien through synaptic?

---

### Post by dragon84 on 2009-11-07
yep, that's the only way to get it. it's not listed in the "ubuntu software center"

---

### Post by Agent ME on 2009-11-07
There are some extra screensaver packages in the repository, maybe they have the screensavers you want? They are [xscreensaver-data-extra](apt:xscreensaver-data-extra) and [xscreensaver-gl-extra](apt:xscreensaver-gl-extra).

---

### Post by dragon84 on 2009-11-07
WOOOOOO!!!!!that's a lot of screensavers. i'm pretty sure the screensaver is in there somewhere now. thanks a lot Agent ME and also thank you soo much RedSingularity for the help. :p[URL="http://ubuntuforums.org/member.php?u=487064"]
[/URL]

---

### Post by RedSingularity on 2009-11-07
Lol, i have to thank Agent ME as well.  I just picked a new screensaver out of that bunch!

---

### Post by T.E.N. on 2012-06-02
> **dragon84 said:**
> hi guys,
i have a fairly new installed ubuntu 9.10 installed on the system and i need help installing opengl screensavers into it. in version 9.04 ubuntu had some neat opengl screensavers installed but they were removed out of 9.10. well i found a site which has these screensavers i wanted at [http://rsxs.sourceforge.net/downloads](http://rsxs.sourceforge.net/downloads). i have no idea how to install them. 

i have:
- downloaded theSource tarball (rsxs-1.0.tar.gz)
- $ tar xzf rsxs-1.0.tar.gz[FONT=monospace]
 [/FONT]$ cd rsxs-1.0[FONT=monospace]
 [/FONT]$ ./configure

and get this message "configure: error: can't compile without OpenGL support".Years later, on Ubuntu 12.04 LTS "Precise Pangolin", the message instead is:[quote=./configure]checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.[/quote]Anyhow, no need to recompile it yourself, as (from [http://rss-glx.sourceforge.net](http://rss-glx.sourceforge.net) rather than the above URL) the [http://www.reallyslick.com/screensavers/](http://www.reallyslick.com/screensavers/) you are looking for can be found in the Ubuntu Software Center / repositories as package rss-glx, so all you need to do is (from the shell, well-hidden as Ctrl-Alt-T in Unity):[quote=/bin/bash]apt-get install rss-glx
kill $(pidof xscreensaver)
rss-glx_install
xscreensaver-demo[/quote]...and OK the restart of the xscreensaver daemon it prompts you for.

The new screensavers thus installed are: Biof, Busy Spheres, Colorfire, Cyclone, Drempels, Euphoria, Feedback, Fieldlines, Flocks, Flux, Helios, Hufo's Smoke, Hufo's Tunnel, Hyperspace, Lattice, Lorenz Attractor, MatrixView, Plasma, Pixel City, Skyrocket, Solarwinds, SpirographX, and Sundancer2
(Helios probably having gained the largest "cult following" over time and across platforms: [http://download.cnet.com/Helios-Screensaver/3000-2257_4-10114363.html](http://download.cnet.com/Helios-Screensaver/3000-2257_4-10114363.html), [www.youtube.com/results?search_query=Helios+screensaver](www.youtube.com/results?search_query=Helios+screensaver)).

You may wish to untick Fiberlamp and FuzzyFlakes from the former less "shiny" installed defaults (many others are surprisingly ticked even though greyed out as "Not Installed").

The new Fieldlines, some patterns of Lattice ("Material - Doughnuts", adding to the Advance >> Command Line: " --texture 3" etc. without the quotes should get rid of these), Lorenz, MatrixView, Plasma, Solarwinds, SpirographX and Sundancer2 probably won't be "everybody's cup of tea", but of course that's precisely what the Preview (full screen to see which ones your graphics hardware can actually handle) and Settings... buttons are for.

---

