---
title: "Can I upgrade ubuntu 12.04 to 12.10"
date: 2012-10-14
forum: General Help
---

### Post by aabed91 on 2012-10-14
Hi all,

Can I upgrade ubuntu 12.04 LTS to ubuntu 12.10?

if not

Can I upgrade it to 12.04.1?

Thanks all

---

### Post by zombifier25 on 2012-10-14
Firstly, 12.04.1 is merely 12.04 with all the latest updates. So it's very likely you're already using 12.04.1.

Secondly, 12.10 is still a **beta** release, so things may break. If you still want to upgrade,
```
update-manager -d
```

---

### Post by jrog on 2012-10-14
> **aabed91 said:**
> Hi all,

Can I upgrade ubuntu 12.04 LTS to ubuntu 12.10?
Yes, but keep in mind that 12.10 has not officially been released yet. It is, however, in the release candidate stage, so there are unlikely to be any huge changes coming down the pipe. See the instructions on upgrading here: [https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta2](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Beta2)

> **aabed91 said:**
> if not

Can I upgrade it to 12.04.1?
I believe that if you have been running 12.04 and have been regularly upgrading, you are already effectively running 12.04.1.

---

### Post by jrog on 2012-10-14
> **zombifier25 said:**
> Secondly, 12.10 is still a **beta** release, so things may break
Well, this may be a bit of a technicality, but according to the Quantal release schedule we are now in the "release candidate" stage, though there was no official release candidate ISO. See the schedule here: [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule). At such a stage, Quantal is hoped to be functionally identical to the final release, and only fixes for very major bugs (if there are any) are supposed to be allowed through.

---

