---
title: "wi-fi not working on fedora 15"
date: 2011-05-27
forum: General Help
---

### Post by rockager on 2011-05-27
i've just installed fedora on my netbook (dual booted with ubuntu) but there is no option of connecting to a wireless network in the network settings menu, my wi-fi connection works perfectly on ubuntu.

what do i do?

---

### Post by rockager on 2011-06-02
i figured it out myself,
i have a Broadcom BCM 4727 network adapter on my computer so i can directly install the driver (as an rpm package) from rpmfusion repository, no hassles!

just use this command to download and install the package:

yum install kmod-wl

---

