---
title: "Ati driver when upgrading to 2.6.31.20"
date: 2010-03-05
forum: General Help
---

### Post by howlingmadhowie on 2010-03-05
Hi everybody. i just got bit by the ati driver after i updated to 2.6.31.20.  basically, X refused to start and refused badly to start. it didn't dump me to a terminal and it locked up the whole system, so i had to press the reset button (phenom 965 with an ati 5750).

i booted with a live cd and reconfigured grub2 to allow me to select an entry. then i moved /etc/X11/xorg.conf to /etc/X11/xorg.conf.old and restarted the computer.

now X started as usual but without the ati driver. I started the restricted hardware manager and reinstalled the ati driver. then everything worked fine :)

---

