---
title: "Zotac GT 430: effects can't be turned off, nor can monitor brightness be changed"
date: 2011-08-03
forum: General Help
---

### Post by LodeRunner on 2011-08-03
New install of 11.04 (using Gnome, not Unity) on a Via Nano Desktop with a Geforce GT430 (Zotac ZT-40602-10L.) Monitor is a 23" Acer, model G245HQabd. Using default recommended driver for the video card.

After installing the graphics driver, effects are automatically turned on. They've slightly laggy, so I go to System=>Preferences=>Appearance to turn them off.  It launches, but **the effects tab is simply missing**. "Theme", "Background", "Fonts", that's it.  

Second issue is my inability to turn down the brightness. Already I am getting severe eyestrain. It's been a long time since I messed with desktops, and I don't recall if there's a special way to change brightness if you're not on a laptop. 

The brightness applet is nonfunctional (laptop only, it seems.)

There is no brightness setting under System=>Preferences=>Power Management (could've sworn there used to be...?) 

There is no brightness setting under System=>Preferences=>Monitors, and my monitor is listed as "unknown."

System=>Admin=>"NVidia X Server Settings"  does see the monitor, listing the model as G245HQ. However, under "X Server XVideo Settings", none of the settings (including brightness) do anything. I can move the slider or manually change the number and it will remember the value, but it's nonfunctional. The values in "X Server Color Settings" do work, but it screws up the picture quality. If I crank brightness down to a comfortable level, everything has a horrible blue-gray tint.

Ideas?

---

### Post by pme 72 on 2011-08-03
Is there a Menu button on the monitor itself that has a brightness adjustment?

---

### Post by pqwoerituytrueiwoq on 2011-08-03
go to Nadia Settings and set it to performance and sync to vblank
my gt 430 does effects on gnome 2 like it is nothing
i set compiz to 30 fps since i cant see a difference between that and 60 in ccsm
i can get up to 53 fps on fish ie @ 500 fish
your chip has a higher "Effective Memory Clock" than mine 1000 more

---

