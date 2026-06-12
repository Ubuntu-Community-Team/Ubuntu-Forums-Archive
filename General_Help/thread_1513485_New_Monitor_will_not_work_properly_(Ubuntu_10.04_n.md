---
title: "New Monitor will not work properly (Ubuntu 10.04 new install)"
date: 2010-06-19
forum: General Help
---

### Post by dpgtfc on 2010-06-19
I have a new Acer H203H running DVI on a GeForce 8500.  My other monitor is an Acer, but a different model and it works just fine (it isn't a widescreen and is using VGA).

My monitor shows up when I have it configured with the NVIDIA X Server Settings utility, but is stuck at 680x480.

The new monitor does require a special driver in a windows environment, but I've no idea how to run the utility or manually install the drivers.  

Any help is greatly appreciated!

---

### Post by cariboo on 2010-06-19
Open a terminal and run:

```
nvidia-xconfig
```

The above command will create an /etc/X11/xorg.conf file, when it's done reboot, to see if that makes a difference.

---

### Post by dpgtfc on 2010-06-19
> **cariboo907 said:**
> Open a terminal and run:

```
nvidia-xconfig
```

The above command will create an /etc/X11/xorg.conf file, when it's done reboot, to see if that makes a difference.

Hey, thanks for the reply!

I tried what you recommended and go the error:

Validation Error: Data Incomplete in file /etc/X11/xorg.conf Undefined Device "(null)" referenced by screen "Default Screen"

---

