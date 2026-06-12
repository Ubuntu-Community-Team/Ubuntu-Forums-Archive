---
title: "Fix dpkg"
date: 2011-10-03
forum: General Help
---

### Post by Orcris on 2011-10-03
I tried installing kubuntu-full, and the package language-pack-kde-sd-base made it freeze, so I quit it using the system monitor. Now dpkg is broken. I tried running sudo dpkg --configure -a, but APT and/or dpkg still won't work. When I run sudo apt-get install anything, I get this error:> E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/How do I fix this?

---

### Post by drs305 on 2011-10-03
Normally it means you have a GUI package manager in use or another package manager running in the background. Close Synaptic, Software Sources, etc and try again. If the lock remains, close all your apps and reboot. This allows a normal shutdown and the lock is usually removed during the shutdown.

---

