---
title: "Drivers for a Atheros AR8132 Ethernet card"
date: 2010-02-05
forum: General Help
---

### Post by RobFS1 on 2010-02-05
My brother brought me a Toshiba P505-S8980 with Windows 7 (64 bit) on it and I installed Ubuntu 9.10 on it, after much trial, and trying to find a edition of the distro that had a compatible graphics driver and resolution. That finaly worked, but now my issue is that I can't find a driver for the Ethernet card (Atheros AR8132) and though I found a driver for the WLAN card, it still doesn't connect. I have heard that there are proprietary drivers available in a couple of repositories for the Atheros card, but I cant connect the machine to the internet, so that doesn't help, and the drivers I have found that are said to be available for the card are either incompatible or uncompilable. Can anyone help?

---

### Post by n0dix on 2010-02-05
Are you tried with the in installation of software driver GUI in Gnome? I think Ubuntu should suggestion some driver to install.

---

### Post by RobFS1 on 2010-02-06
Which GUI are you referring to?

---

### Post by n0dix on 2010-02-06
I mean, the properties driver. In System -> Administration -> Propertie Drivers. I don't remember very well.

---

### Post by RobFS1 on 2010-02-06
Yes I have tried that, but as I said in my first post, that wont work because I am not connected to the internet.

---

### Post by Sylslay on 2010-02-15
What ubuntu , are You use :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/415358](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/415358)

they said: Impact: Atheros AR8132 / L1c Gigabit Ethernet Adapter fails to operate
in Jaunty due to the lack of driver support.

Fix: Backport the atl1c driver from Karmic back to Jaunty.

---

### Post by dfavro on 2010-05-06
Hi, don't know if you're still having this issue, but in case you or anyone else is:

OP said he was using 9.10, although also said he searched for an "edition of the distro" that supports his hardware (not sure what that means).  Anyhow, I'm surprised that 9.10 didn't work out-of-the-box for AR8132 since I believe that that the _desktop_ installation media contains a working driver (atl1c).  If not, 10.04 does.  In both cases, however, you either must install from the so-called "desktop" installation media, or if installing from "alternate" media, apply the work-around listed in bug #557130:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557130](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557130)

Once you've installed, connect to internet using a wire, and let the GUI install the proprietary wireless drivers if necessary, as was previously posted here; from then on, failure to connect via wireless is likely not a driver issue, but something else.

Hope that helps.

---

