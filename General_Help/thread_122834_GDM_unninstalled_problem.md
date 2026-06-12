---
title: "GDM unninstalled problem"
date: 2006-01-28
forum: General Help
---

### Post by Khanater on 2006-01-28
Hi guys! I have a problem with gdm, because accidentally was erased.
I was trying to intall Opera web browser and need somes dependencies.
and i execute **sudo apt-get -f install** in a terminal with this i get that dependencies, but the **apt-get** delete all this packages:
> 
  bum firestarter gdm gksu gnome-app-install gnome-netstatus-applet
  gnome-system-monitor gnome-volume-manager hwdb-client libgksu1.2-0
  libgksuui1.0-0 python-gnome2-extras python2.4-gnome2-extras qtparted
  serpentine ubuntu-desktop x-window-system-core xbase-clients
  xkeyboard-config xsm
and now, when i try to reinstall gdm with **sudo apt-get install gdm**
download all this packages: 
> 
libgksu1.2-0 1.2.5a-1ubuntu1
xbase-clients 6.8.2-10.1
libgksuui1.0-0 1.0.3-2ubuntu2
gksu 1.2.4-1ubuntu8
gdm 2.6.0.7-0ubuntu7


and the the installation crashes because say that that the dependencies cant be resolved and return exit code 1.
> E: xbase-clients: subprocess post-installation script returns erro code 74
E: libgksu1.2-0: dependencies problems - without configuration
E: libgksuui1.0-0: dependencies problems - without configuration
E: gksu: dependencies problems - without configuration
E: gdm: dependencies problems - without configuration


Also try reinstalling gdm with sudo synaptic and get the same error.

Any idea around?

Thanks in advance!

---

### Post by superhew on 2006-01-28
have you tried:
sudo apt-get install ubuntu-desktop

that might work, worth a try at least.

---

### Post by Khanater on 2006-01-28
Already resolved this problem updating the **sources.list** with others servers and doing this:
> 
sudo apt-get update
sudo apt-get install gdm


Thanks!

---

