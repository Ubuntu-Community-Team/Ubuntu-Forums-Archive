---
title: "ubuntu 10.04 issues"
date: 2011-12-11
forum: General Help
---

### Post by masterrob213 on 2011-12-11
i recently upgraded to ubuntu 10.04 and its already giveing me huge issues after awhile ill be on it for awhile then it flashes off to the ubuntu screen but its disfigured completely then it flashes again then all you see is white streeks goin down the computer down to at least half of the screen and the keyboard quits working. ive already tried reinstalling it and i still get the same thing

---

### Post by Penguinnerd on 2011-12-11
That sounds like video card related issues.

What kind of PC is this? What's the video card?

---

### Post by masterrob213 on 2011-12-11
its a dell computer but im not sure on the video card how would i find out?

---

### Post by gennatolls on 2011-12-11
```
lspci | grep VGA
```

For more information:

```
sudo lshw -C video

```

Official Ubuntu Page: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by masterrob213 on 2011-12-11
[SIZE=2]description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:ff680000-ff6fffff
[/SIZE]

---

### Post by oldtimer7777 on 2011-12-11
I believe the intel driver you need is actually updated in 11.04 not 10.04..

> **masterrob213 said:**
> [SIZE=2]description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:ff680000-ff6fffff
[/SIZE]

---

### Post by masterrob213 on 2011-12-11
so should i just upgrade again to 11.04?

---

### Post by gennatolls on 2011-12-11
Go to 11.10, its more refined.

---

### Post by masterrob213 on 2011-12-11
i tried that and i got like keyword not recognized in config i was doing the usb way

---

### Post by fdrake on 2011-12-11
how about before doing the "big jump" try to do the small steps:
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-cache search linux-image

```
try to install the latest linux images and see if that solves the problem. 10.04 is more stable than 11 and you will find more support in fixing issues (and upgrading your sys to 12.04-LTS next year).

---

### Post by masterrob213 on 2011-12-11
Invalid operation safe-upgrade

---

