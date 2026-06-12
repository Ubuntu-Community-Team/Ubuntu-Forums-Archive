---
title: "How to mount an external sata hd on Ubuntu 11.10?"
date: 2012-03-03
forum: General Help
---

### Post by Squerl101 on 2012-03-03
Hey guys, i just bought a 2.5 inch sata drive enclosure, and i plugged it in to my laptop with 10.11 32 bit, and it doesnt show up. So i have to mount it myself. I'm a noob at mounting, so can someone tell me how to do it? Thanks.

---

### Post by travisf on 2012-03-03
You can use the package "scsi-tools" which includes the script 'rescsan-scsi-bus'. You could make a new menu entry and call the script with gksudo.

My menu entry is 'xterm -e gksudo /sbin/rescan-scsi-bus.sh'

I'm not sure which version is in the repository. I use the latest from 'http://www.garloff.de/kurt/linux/'

---

