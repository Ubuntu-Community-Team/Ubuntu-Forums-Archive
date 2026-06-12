---
title: "CHanging brightness through command line"
date: 2011-07-05
forum: General Help
---

### Post by gunjannigam on 2011-07-05
Hi,
I recently bought a new Toshiba NB 250 netbook and tried to install ubuntu 8.04 on it. I succeeded with the installation but Ubuntu 9.04 didn't recognize my desktop resolution(1024*600). System only had default 800*600 resolution. I tried to change it by altering XOrg but wasn't successful in that. When I wanted to change the brightness of my screen using command line setpci command ```
setpci -s 00:02.0  F4.B=xx
``` didn't work but altering my brightness file in /proc/acpi/video ```
echo -n 70 > /proc/acpi/video/IGD0/LCD/brightness
``` worked. Also I wasn't able to connect to any network neither through Wired or Wireless connection
So I switched to Ubuntu 10.04 and voila it detected my monitor resolution and wireless networks as well. But I can't find any video folder in /proc/acpi. They had ac_Adapter, battery,embedded_contoller, power_resource,process,thermal zone. How can i adjust brightness now in Ubunutu 10.04. Obviously stpci command still doesn't work either

---

