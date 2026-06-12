---
title: "Ubuntu wont boot"
date: 2009-09-05
forum: General Help
---

### Post by tmorphius on 2009-09-05
I installed ubuntu 9.04 desktop last night on my laptop, and everything seems to go fine, on the first reboot, but then i installed all the programs i use, and when you go to reboot it passes the ubuntu logo loading screen and then just starts flashing with random ****... This isnt the first time this has happened, and im not sure what to do, ive tried auto-fixing graphics problems and repairing broken packages in recovery mode but still no luck

heres a link to a video of it booting on youtube:
[http://www.youtube.com/watch?v=zp2iW-gNdHQ]("http://www.youtube.com/watch?v=zp2iW-gNdHQ")

anyone help?

---

### Post by DeMus on 2009-09-05
> **tmorphius said:**
> I installed ubuntu 9.04 desktop last night on my laptop, and everything seems to go fine, on the first reboot, but then i installed all the programs i use, and when you go to reboot it passes the ubuntu logo loading screen and then just starts flashing with random ****... This isnt the first time this has happened, and im not sure what to do, ive tried auto-fixing graphics problems and repairing broken packages in recovery mode but still no luck

heres a link to a video of it booting on youtube:
[http://www.youtube.com/watch?v=zp2iW-gNdHQ]("http://www.youtube.com/watch?v=zp2iW-gNdHQ")

anyone help?

This is a graphic driver problem. In safe mode type 
```
lspci | grep VGA
```
and report the outcome here please. It's a way to determine which graphic card you have.

---

### Post by tmorphius on 2009-09-05
> **DeMus said:**
> This is a graphic driver problem. In safe mode type 
```
lspci | grep VGA
```
and report the outcome here please. It's a way to determine which graphic card you have.

it says:
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200m 5955 (PCIE)

---

