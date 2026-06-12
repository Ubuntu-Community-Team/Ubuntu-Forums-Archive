---
title: "No boot screen"
date: 2009-07-16
forum: General Help
---

### Post by toehead2 on 2009-07-16
I am running Hardy Heron on a Dell Inspiron 1100 laptop, my problem is there isn't a boot screen at start up, at least I believe this is the boot screen, it is the Ubuntu logo with the progress bar. Running the live cd it appears as normal however booting Ubuntu from the hard drive it isn't there, just a dark screen until the brown log-in screen appears. 
I have had this problem since I switched to Ubuntu, and have reinstalled Ubuntu a couple of times.
Any help?

---

### Post by sedawk on 2009-07-16
You can compare the graphics driver used by the Live-CD 
to the one installed on the harddrive (/etc/X11/xorg.conf).

Most likely the Live-CD uses a different graphics driver
than your installed Ubuntu.
(The Live-CD uses robust but slow (generic) graphics drivers, while
 the one on the harddisk is most likely a special one for
 your graphics chipset. It should be possible to switch (back)
 to the driver used by the Live-CD, but then graphics might run
 slower or you do not have 3D enhancements).

---

