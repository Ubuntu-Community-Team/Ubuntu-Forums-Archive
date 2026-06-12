---
title: "Best Ubuntu version for embedded environment?"
date: 2011-06-09
forum: General Help
---

### Post by rainbow82 on 2011-06-09
Hi, I am in need of an Ubuntu that can run on a single board computer. It has AMD Geode GX-MMX 500MHz processor, 500MB RAM and a flash card module.

I need a minimal ubuntu install without any GUI. I tried live CD Ubuntu 11.04 desktop edition, runs fine, but after its installation on a USB flash drive, the system does not boot. The server edition 6.06 looks for a CD drive which the system does not have.

Which type/version of Ubuntu would be best suited for this kind of environment?

Thanks

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **rainbow82 said:**
> Hi, I am in need of an Ubuntu that can run on a single board computer. It has AMD Geode GX-MMX 500MHz processor, 500MB RAM and a flash card module.

I need a minimal ubuntu install without any GUI. I tried live CD Ubuntu 11.04 desktop edition, runs fine, but after its installation on a USB flash drive, the system does not boot. The server edition 6.06 looks for a CD drive which the system does not have.

Which type/version of Ubuntu would be best suited for this kind of environment?

Thanks

I would try installing from from the command line with an Alternative Installation Disc of Ubuntu 10.10.  Use 32-bit in case you need to wrap any 32-bit drivers too.  It really depends on what you are going to use it for I guess. :) 

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by jerrrys on 2011-06-09
also

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by seawolf167 on 2011-06-09
If the minimal version jerrrys posted isn't what you are looking for you could also try the Ubuntu 10.04 LTS server version. It ships without a desktop and a lot of the misc programs the desktop version has. It is larger and has a number more packages than the minimal version though.

---

