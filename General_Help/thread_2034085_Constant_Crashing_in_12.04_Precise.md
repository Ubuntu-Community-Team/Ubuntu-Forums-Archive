---
title: "Constant Crashing in 12.04 Precise"
date: 2012-07-27
forum: General Help
---

### Post by thorner on 2012-07-27
Can anyone help me with a huge problem I have? My computer is constantly crashing, sending me back to the login screen. I have searched and tried everything suggested, but to no avail. 

I've finally decided to post here for some help.

If I can't figure it out soon, I will have to rollback/downgrade to 11.10 - which worked fine for me.

Thanks.

AMD AthlonII X4 640
Ubuntu 12.04 x64
nVidia 8500GT with 302.17 driver
Kernel 3.2.0-27-generic

---

### Post by Bobhuber on 2012-07-27
> **thorner said:**
> Can anyone help me with a huge problem I have? My computer is constantly crashing, sending me back to the login screen. I have searched and tried everything suggested, but to no avail. 

I've finally decided to post here for some help.

If I can't figure it out soon, I will have to rollback/downgrade to 11.10 - which worked fine for me.

Thanks.

AMD AthlonII X4 640
Ubuntu 12.04 x64
nVidia 8500GT with 302.17 driver
Kernel 3.2.0-27-generic
Try using the 295.59 Nvidia drivers

---

### Post by thorner on 2012-07-28
I was initially using the 295.59 drivers that installed with Precise and had the same issues.
I will rollback and see what happens...

---

### Post by thorner on 2012-07-28
well, after many hours of hacking away at the command line, I somehow managed to rollback to driver 295.49

About 5 minutes after rebooting with 295.49, I was sent to the login screen!

Happens in 2D, Gnome, Gnome Classic and Gnome Classic (no effects)

I even had the idea that my machine was overheating, so removed the side panel and have a couple more temp fans keeping things super cool. Still crashes!

---

