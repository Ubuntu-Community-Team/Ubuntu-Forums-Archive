---
title: "nvidia"
date: 2006-06-10
forum: General Help
---

### Post by wireless on 2006-06-10
hey all
after stupidly installing nvidia xconfig and driver from synaptic i cant login with grphical enviroment. obviously i didnt know what i was doing. 

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun 10 13:32:36 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Intel Corporation 82852/855GM Integrated Graphics Device"

how can i correct this please?
thnx in advance!!

---

### Post by starkes on 2006-06-10
maybe try this:
sudo apt-get install nividia-glx
sudo nvidia-glx-config enable

if that doesnt work, check in /etc/X11/ for a backup of xorg.conf, and then restore it by copying it over xorg.conf

---

