---
title: "Problems with ndiswrapper -m"
date: 2010-08-13
forum: General Help
---

### Post by BriceHulse on 2010-08-13
Hi, everyone. I'm trying to install the bcm43xx drivers for my Linksys WMP54Gv2 with ndiswrapper. When I install the drivers with *ndiswrapper -i bcmwl5*, I get the following output:
> 
installing bcmwl5
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

Here's my problem: When I type *ndiswrapper -m*, I get the following output:
> 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive



FYI, I get the following output when running *ndiswrapper -l*
> 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: ssb)


Does anyone know what the problem is with *ndiswrapper -m*?

Thanks

---

