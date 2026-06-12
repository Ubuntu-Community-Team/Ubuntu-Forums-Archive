---
title: "Classic Desktop breaks, Unity works fine"
date: 2011-06-14
forum: General Help
---

### Post by d1g1t on 2011-06-14
When I log into the classic desktop, nothing other than the wallpaper appears,and when I ctrl+alt+f1 and check top/htop
it shows that both X and gnome-panel are using 100% cpu

I'm able to use unity, but the top panel gets unreponsive after a while and top/htop shows unity using up 100% cpu. a unity --replace fixes it temporarily

I really prefer the classic desktop. is this possible to fix without having to reinstall?

I'm using ubuntu 11.04 64bit with an ati card.
the system has been working fine since natty alpha3
The problem appears to have started after a certain update and I'm unable to find it in synaptic's history (the update also contained the firefox 5beta upgrade from natty-proposed)

---

### Post by d1g1t on 2011-06-14
odd. All my issues seem to automatically get fixed once I post the problem on these forums >:(

I'm not sure which one of these fixed it
* enabled xorg edgers ppa
* installed the latest ati driver ati-driver-installer-11-5-x86.x86_64
* purged the xorg edgers ppa
* ran sudo dpkg-reconfigure xserver-xorg

---

