---
title: "Nvidia TwinView and Gvfs-trash and Nautilus High CPU"
date: 2011-09-01
forum: General Help
---

### Post by liferules on 2011-09-01
Okay so I got my new Port Replicator today (Dell E210) for my new Dell Precision Mobile Workstation M4600 (i7 2760QM, 16GB RAM, 750GB HD, Nvidia Quadro 2000M 2GB, 11.04 Gnome Classic).

The problem is that as soon as I enable Nvidia Twinview, my mouse cursor spins as busy almost constantly. After looking around in Htop I realized that Gvfsd-trash was using 100% of one CPU and Nautilus processes were multiplying. In this state Nautilus will not even open. I tried killall but it just starts all over again. The only fix that I am able to work out is to leave Twinview and use only one monitor. Then the system returns to normal.... 

Any ideas? As a graphics professional I really would like to use two monitors... 

Chuck

---

