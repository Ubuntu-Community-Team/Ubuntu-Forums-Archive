---
title: "facebook very slow amd64 flash?"
date: 2009-06-25
forum: General Help
---

### Post by misha680 on 2009-06-25
Hi:

If anyone has any suggestions I have Ubuntu 8.04 running on amd64. Facebook scrolling is very slow. I installed some greasemonkey scripts but doesn't help. I use the Adobe Flash 10 alpha but I don't think this is the cause. I have nvidia proprietary driver.

Thanks
Misha

---

### Post by misha680 on 2009-06-25
Filed bug
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/392350](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/392350)

---

### Post by Arup on 2009-06-25
Your problem is the video driver. The older 169xx drivers have issues with smaller pixmaps which lead to scrolling issues, you need to install latest nvidia 185xx series to resolve this particlular issue.

---

### Post by misha680 on 2009-06-26
> **Arup said:**
> Your problem is the video driver. The older 169xx drivers have issues with smaller pixmaps which lead to scrolling issues, you need to install latest nvidia 185xx series to resolve this particlular issue.

Thanks. I installed new one and it seems to do the trick.

Misha

---

### Post by misha680 on 2009-07-09
> **Arup said:**
> Your problem is the video driver. The older 169xx drivers have issues with smaller pixmaps which lead to scrolling issues, you need to install latest nvidia 185xx series to resolve this particlular issue.

So I seem to be getting horrible screen flicker (pretty random, screen starts flickering, computer becomes unresponsive although it is not kernel crash I take it because power button still eventually leads to shutoff - sometimes) with 185.

If I downgrade seems to go away.

Any advice? What video card do you have? I have Quadro NVS 135m.

Thank you
Misha

---

### Post by misha680 on 2009-07-25
Dell Replaced my motherboard and fans now 185 works great. Thank you.

Misha

> **misha680 said:**
> So I seem to be getting horrible screen flicker (pretty random, screen starts flickering, computer becomes unresponsive although it is not kernel crash I take it because power button still eventually leads to shutoff - sometimes) with 185.

If I downgrade seems to go away.

Any advice? What video card do you have? I have Quadro NVS 135m.

Thank you
Misha

---

