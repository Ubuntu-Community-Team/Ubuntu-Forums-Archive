---
title: "How to change wireless driver"
date: 2011-05-18
forum: General Help
---

### Post by Pacopag on 2011-05-18
Hi.  On an older release, my wireless worked fine, and it was using the broadcom-wl driver.  Now on a newer release, the driver seems to be b43, but the card is not being detected.

How can I change the driver so that it uses wl by default?

---

### Post by mikewhatever on 2011-05-18
Uninstall b43-fwcutter and anything that starts with firmware-b43..., and install the bcmwl-kernel-source package. Reboot.

---

### Post by Pacopag on 2011-05-18
I did as you said.  It's still telling me that the driver is b43-pci-bridge

---

### Post by wildmanne39 on 2011-05-18
> **Pacopag said:**
> I did as you said.  It's still telling me that the driver is b43-pci-bridge
Hi, try
sudo apt-get --purge remove <package name> without the symbols.

---

### Post by mikewhatever on 2011-05-18
Pacopag, what's telling you that? Have you tried reboting the machine?  If the STA driver still doesn't load, please post the outputs of the following commands:
```
dpkg -l | grep -e bcmwl -e b43

lsmod | grep -e wl -e b43
```

---

### Post by Pacopag on 2011-05-19
Both commands spew no output.

Also, I couldn't find the bcmwl-kernel-source package.  I installed broadcom-sta-common package instead.  The description said that it contained the drivers for my card.

---

### Post by mikewhatever on 2011-05-19
It doesn't look like you are running Ubuntu there. I am pretty positive that bcmwl-kernel-source is present in all currently supported Ubuntu versions and broadcom-sta-common is not. Searching for broadcom-sta-common turned up it's a Debian non-free package, in which case, it's irrelevant what the package is called in Ubuntu.
[http://packages.debian.org/unstable/admin/broadcom-sta-common](http://packages.debian.org/unstable/admin/broadcom-sta-common)

---

### Post by Pacopag on 2011-05-19
Looks like I'm busted.  You're right.  I'm running AntixM11.  I figured since it's debian-based the solution might be the same.

---

### Post by mikewhatever on 2011-05-19
AntiX is cool. Anyway, how is the STA driver working for you? Did you have to add the non-free repository to install it?

---

### Post by Pacopag on 2011-05-19
It didn't work.  Everytime I check my card via "inxi -F" the b43-pci-bridge driver always shows up.  Even if I go to synaptic and completely remove any package related to b43, then reboot.  I think that if I could completely uninstall the card and its driver, I might be able to install the driver from the Dell website using ndiswrapper.  The problem is that I can't seem to uninstall the b43 driver and it always defaults to b43.

---

### Post by Pacopag on 2011-05-19
Here is something curious.  In AntixM8.5 the wireless works, and it says that my wireless chipset is BCM4328 with driver wl.

In AntixM11, which I'm trying to use now, the wireless doesn't work, and it says that my wireless chipset is BCM4321 with driver b43-pci-bridge.

Does that help with anything?

---

### Post by mikewhatever on 2011-05-19
Keep in mind that all the commands above were for *buntu, which means you may have been uninstalling non-existing packages. Actually, just checked, and the naming is the same in Debian.
[http://packages.debian.org/search?searchon=names&keywords=b43](http://packages.debian.org/search?searchon=names&keywords=b43)
Regardless, you should be able to blacklist the b43 module. In *buntu it's as simple as adding a line to /etc/modprobe.d/blacklist.conf, and probably the same or very similar in AntiX.

---

