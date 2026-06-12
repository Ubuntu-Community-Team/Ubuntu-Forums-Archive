---
title: "dmraid remove a hotspare"
date: 2011-11-26
forum: General Help
---

### Post by styx666 on 2011-11-26
Hi folks,

i accidentially added a drive (my system disk) as a hotspare to an array.

Can someone give me a hint how to non-destuctively remove that device from he array?
The manpage kind of gives me nothing on this...

/dev/sdg: isw, "isw_cffefebihf", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sdf: isw, "isw_cffefebihf", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sde: isw, "isw_cffefebihf", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sdd: isw, "isw_cffefebihf", GROUP, ok, 2930277166 sectors, data@ 0
/dev/sdc: isw, "isw_cffefebihf", GROUP, ok, 2930277166 sectors, data@ 0

/dev/sdb: isw, "isw_beceeajcgc", spare, ok, 2930277166 sectors, data@ 0
**/dev/sda: isw, "isw_dfgbbhdahd", spare, ok, 117231406 sectors, data@ 0**


:) Regards,

Styx

Edit: i didn't notice till now that it added the last two devices each to *new* set, instead of adding them to the existing one..

This fixed i for me - by actually removing the wrongly created set:
dmraid -x isw_dfgbbhdahd_/dev/sda

---

