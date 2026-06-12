---
title: "sda into hda"
date: 2010-07-05
forum: General Help
---

### Post by shahxaibhaq on 2010-07-05
hello,
i been using GParted for very long time for resizing & formatting partitions but suddenly now my HDD is changed from hda into sda....
guys is there any way to change it back to hda!!!!

---

### Post by sisco311 on 2010-07-05
The IDE subsystem in the linux kernel (>= 2.6.19) has been functionally replaced by the PATA subsystem which uses the sdX naming convention.

[http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce](http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce)

---

