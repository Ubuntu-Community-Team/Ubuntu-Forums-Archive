---
title: "Preparing for Webcams in devfs"
date: 2009-07-26
forum: General Help
---

### Post by bcschmerker on 2009-07-26
By now ye probably know about the Webcams supported by the [LinUX USB Video Class Project](http://linux-uvc.berlios.de/), sponsored by [Berli OS](http://www.berlios.de/).  I recently purchased a 1280x1024 Dynex webcam to test UVC Video in Kernels 2.6-up on Ubuntu 8.04-LTS (current Kernel as of 25 July 2009: 2.6.24-24.56-generic); the problem is the lack of applicable device nodes in DevFS (e.g., no /dev/video0).  How does one go about building the necessary nodes, which may involve modifying boot scripts (which I have to do anyway to fix a twice-start condition with /SBin/Portmapper during normal boot)?

---

