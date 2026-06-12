---
title: "Repairing ubuntu installation externally?"
date: 2011-09-08
forum: General Help
---

### Post by Xtensity on 2011-09-08
So, my ubuntu 10.10 just crashed on me... Randomly. The screen went black and all the lights on my keyboard started flashing at consistent intervals.

I had to manually shut it off. When I did so, I have been unable to boot correctly. It keeps going into low graphics display mode :(. 

Right now, I am logged into to another 10.10 partition that I had as a backup, and I'm wondering if there is any way I can access/repair my other 10.10 installation from this one. I got access to the consol in recovery mode or whatever, but I don't know much about ubuntu commands, and more importantly, I don't know what got broken.

It said something to do with my graphics drivers and display settings :(.

Edit:

I already did repair broken packages from the console but that didn't fix the problem any.

---

### Post by sum1nil on 2011-09-08
Can you access the broken install from your backup?
You may want to reinstall your graphics driver on the broken installation.
You could download the driver from their website and copy it over to the other partition and then boot that one up. In recovery console (scroll down) to login as root shell.

Go to where you copied the driver (you may have to change permissions on the file eg chmod 755 name.of.file) and then run it typically by ./name.of.file.

With any luck, re-installing the driver will fix the problem.

---

### Post by Bucky Ball on 2011-09-08
Boot into the broken install in low-graphics. Get online and do an update (System>Administration>Update Manager), then System>Administration>Additional Drivers. Anything there for your graphics card?

If there is and disabled, enable. ;)

---

