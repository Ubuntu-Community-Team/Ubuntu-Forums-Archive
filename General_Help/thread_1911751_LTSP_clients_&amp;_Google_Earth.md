---
title: "LTSP clients &amp; Google Earth"
date: 2012-01-19
forum: General Help
---

### Post by theller on 2012-01-19
I have ubuntu 10.04 server with ltsp clients. I am having trouble loading google earth on the clients. No matter how I try, it always installs on the server and not in the client image. I tried:

sudo chroot /opt/ltsp/i386 apt-get install googleearth-package
sudo chroot /opt/ltsp/i386 apt-get install googleearth

I tried using sudo nautilus and moving the .deb to /opt/ltsp/i386/ then doubleclicking

I have also tried and modified commands from many sites, still no luck.

Has anyone done this?

---

### Post by dcstar on 2012-01-20
> **theller said:**
> I have ubuntu 10.04 server with ltsp clients. I am having trouble loading google earth on the clients. No matter how I try, it always installs on the server and not in the client image. I tried:

sudo chroot /opt/ltsp/i386 apt-get install googleearth-package
sudo chroot /opt/ltsp/i386 apt-get install googleearth

I tried using sudo nautilus and moving the .deb to /opt/ltsp/i386/ then doubleclicking

I have also tried and modified commands from many sites, still no luck.

Has anyone done this?

[https://wiki.ubuntu.com/LTSPLocalAppSetup](https://wiki.ubuntu.com/LTSPLocalAppSetup)

---

