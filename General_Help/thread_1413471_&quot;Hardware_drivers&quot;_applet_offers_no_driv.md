---
title: "&quot;Hardware drivers&quot; applet offers no drivers, despite Nvidia hardware present"
date: 2010-02-22
forum: General Help
---

### Post by Objekt on 2010-02-22
I'm having a really odd problem with Ubuntu 8.04.4 LTS.  After finishing the install & getting to the desktop, I was not offered the chance to install the proprietary Nvidia drivers.  When I manually run the "Hardware Drivers" applet from the system menu, the list of drivers to install is blank.

What's happening here?  The system definitely does have hardware that could use the Nvidia driver package, in the form of a GeForce 9800 GTX+ video card.  

Last month, I built another system having the Nvidia GeForce 7025 built-in video hardware & installed Ubuntu 8.04.3 LTS.  I was offered the chance to install the proprietary Nvidia drivers as soon as I got to the desktop the first time.  

Why the difference?

I tried to install the Nvidia 190.53 Linux drivers package, but it didn't work.  While it looked like it worked, I got a garbled screen on the next startup, and had to run a manual X configuration utility to get a usable desktop.

FWIW the system has 2 monitors connected, one a 21" CRT and the other a 23" widescreen LCD.  This is exactly the same setup I had when I installed Ubuntu 9.10 a few months ago, and I didn't have any problems getting the Nvidia drivers to work in that case.  Version 185 was offered automatically by the "Hardware Drivers" applet, and I later manually upgraded to the 190.53 package.

---

### Post by howefield on 2010-02-23
> **Objekt said:**
> I'm having a really odd problem with Ubuntu 8.04.4 LTS.  After finishing the install & getting to the desktop, I was not offered the chance to install the proprietary Nvidia drivers.

Sometimes you have to update your package list before the drivers show in Hardware Drivers, you mentioned you had just "finished installing".

Open Synaptic Package Manager and press the reload button, or open a terminal and type

```
sudo apt-get update
```

---

### Post by Objekt on 2010-02-23
Well, I did let it (the 8.04.4 install) download & install a bunch of updates last night, then reboot.  Still, the "Hardware Drivers" applet detects nothing.

What's further puzzling is that the Nvidia .run package did not work.  When I dropped to the command line, stopped the X server, and ran the Nvidia .run package, everything went smoothly.  I saw no error messages, so I don't know why the Nvidia drivers aren't being used.  This one has me stumped.

---

