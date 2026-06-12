---
title: "ATI mobility radeon x300 driver installation on Jaunty"
date: 2009-08-26
forum: General Help
---

### Post by Hoobes1 on 2009-08-26
i found a driver on [www.ati.com](www.ati.com) , but somehow can't find a way to install it on Ubuntu 9.04. is there any way i can install it?

---

### Post by P4man on 2009-08-26
Nope, you didnt find a driver for your X300 for jaunty. ATI no longer supports your card. You can only use older drivers that work with ubuntu 8.10 (and older) or you have to use the opensource driver (which you already have).

Sorry to say..:s

---

### Post by Hoobes1 on 2009-08-26
oh ok, well that explains it then XD how can i get the 8.10 driver and how can i install it, though?

---

### Post by P4man on 2009-08-26
8.10 driver ? it doesnt work on jaunty (9.04).
You'd have install **ubuntu 8.10** and then you can install the driver easy enough through System > admin > hardware drivers 

Either that, or using the opensource one's you have (not working well ?) or a new videocard Im afraid.

---

### Post by Hoobes1 on 2009-08-26
yeah, thought so that i'd have to do that. oh well, thanks! =)

---

### Post by ssri on 2009-08-27
> **P4man said:**
> 8.10 driver ? it doesnt work on jaunty (9.04).
You'd have install **ubuntu 8.10** and then you can install the driver easy enough through System > admin > hardware drivers 

Either that, or using the opensource one's you have (not working well ?) or a new videocard Im afraid.

If one is simply dying to use fglrx in Jaunty, you can always downgrade xserver from 1.6.x to 1.5.x, install ATI's Catalyst 9.3 drivers and pin/hold those packages either in /etc/apt/preferences, synaptic or whichever program/gui you use to manage your packages.  Note, there is a lot of CLI-work involved.  

Here is the guide:

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

All I can say is that I have a Mobility Radeon x2300 (R500) chip and I'm running Catalyst 9.3 in Jaunty with KDE 4.3.0 installed (kernel: 2.6.28-15.49).  3D performance is fine, as I can run googleearth and play nexuiz flawlessly.  Also, I can view send out video to my TV quite easily using Catalyst control center.  TVOut support is flaky with the latest opensource drivers.  Probably the reason why I stuck with Catalyst 9.3. 

That said, I would recommend that anyone who tries to use this method be comfortable using the CLI if anything goes downhill.  Definitely not for novices or the faint of heart!

```
~$ distro
Linux o-toro 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty
~$ fglrxinfo
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X2300
OpenGL version string: 2.1.8543 Release

```

---

### Post by Hoobes1 on 2009-08-29
thanks! =)

---

### Post by KinGnu on 2011-03-16
Excellent... How about in lucid lynx?

---

