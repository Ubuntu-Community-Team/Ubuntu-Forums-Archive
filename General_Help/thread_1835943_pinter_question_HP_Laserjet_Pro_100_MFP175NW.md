---
title: "pinter question HP Laserjet Pro 100 MFP175NW"
date: 2011-08-30
forum: General Help
---

### Post by cotcot on 2011-08-30
Can anybody confirm if this printer functions well and is easy to install under 11.04 64 bit ?

According to the [[COLOR="Blue"]hplip site[/COLOR]]("http://hplipopensource.com/hplip-web/models/color_laserjet/hp_laserjet_100_colormfp_m175b.html") it should work by downloading an additional (proprietary) driver. But I cannot find if it is available for 64 bit. The connection to a wifi (common linksys router) is not confirmed. I consider buying one but prefer to read a user confirmation before.

Thanks

---

### Post by searchfgold6789 on 2011-08-30
The rule is, generally,

[LIST]
[*]32 bit code works on 64 bit machines.
[/LIST]

---

### Post by cotcot on 2011-09-04
I bought the printer. The default hplip version does not know the printer because is a too new type. I installed the latest version from the hplip site. The site proposes a download in function of the distro and its version : that is nice. The download is a script to automatically compiles a tar after checking dependencies. There was 1 mismatch. The script could not find a python-devel package. But that can be solved through synaptic.

Getting the wireless working asked some search work. Finally I installed the printer on a windows machine. The soft from the CD "configured" the printer to recognise my router. Maybe it is possible in linux but i am not specialized in this. Then after installing samba it was easy by adding a new printer and following the instructions.

---

