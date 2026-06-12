---
title: "Error with LVM2 and/or EVMS"
date: 2006-01-23
forum: General Help
---

### Post by greyhound4334 on 2006-01-23
Hi,

I suspect this is a longshot, but I'll ask anyway.

I've installed lvm2 (logical volume manager), but I don't remember installing evms.  It looks like evms may come pre-installed as part of ubuntu_base.

I recently upgraded to a 2.6.15 kernel, and started seeing these messages in my dmesg output:

[17179593.368000] device-mapper: dm-linear: Device lookup failed
[17179593.368000] device-mapper: error adding target to table

They get repeated about 10 times.

Googling around shows these errors coming from some evms-related problems.  It started getting pretty deep, especially since I don't *think* I need/use evms (I certainly don't use it explicitly; but there is some kind of relationship between lvm2 and device_mapper, and between device_mapper and evms and the dependencies aren't clear to me).  The solution offered on the evms web site was to apply a patch, but the docs were spotty, it seemed like it was targeted to an early 2.6 kernel, and I suspected it might do more harm than good.

With that as background, is anyone else seeing this error?  Or know what it means?  I can't see any direct consequences, but I always hate to just ignore such ugly stuff in my system logs, and I do have some mysterious problems (with mythtv) that might *possibly* be related.

Does anyone know if I can safely remove evms (when I try it, apt wants to also remove ubuntu_base, which is a virtual package, that supposedly can be safely removed)?  Or might there be other consequences of removing evms and ubuntu_base that I need to be aware of?

Thanks for any advice.

Cheers,
john

---

