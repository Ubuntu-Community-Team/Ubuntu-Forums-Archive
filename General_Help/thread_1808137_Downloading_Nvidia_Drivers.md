---
title: "Downloading Nvidia Drivers"
date: 2011-07-19
forum: General Help
---

### Post by DEdesign57 on 2011-07-19
I have an Nvidia GTS 250. In windows I have the latest drivers installed and up to date. In Ubuntu I have not done this.

1. In Ubuntu how do I get the latest Nvidia drivers for my card?
2. Will they be the same as the current ones already installed?
3. And will doing so damage at all the state of the drivers that are already on the card, that is that I downloaded and installed in windows? (eg: over-write of any sot)

This is my first time trying to get something on my computer that is not from the software center in Ubuntu so please explain in detail.

Thanks in advance.

---

### Post by Quackers on 2011-07-20
Run Additional Drivers and install the nvidia-current(Recommended) driver.
No it will not be the same as the Windows Nvidia driver.

---

### Post by 2F4U on 2011-07-20
With respect to your point 3.:
Installing drivers in Ubuntu will not damage anything in Windows since Ubuntu and Windows are installed on seperate partitions.

---

### Post by timgood on 2011-07-20
> **2F4U said:**
> With respect to your point 3.:
Installing drivers in Ubuntu will not damage anything in Windows since Ubuntu and Windows are installed on seperate partitions.

And indeed the drivers are not installed on the card itself, but on the HDD.

---

### Post by DEdesign57 on 2011-07-20
I ran additional drivers and it says my version is current. And my only option is to remove not install, but it also says:
This driver is activated but not currently in use.
Is that bad or am I okay?

---

### Post by flipper T on 2011-07-20
ignore that

it is a known issue & a false report & is nothing to worry about

---

### Post by pqwoerituytrueiwoq on 2011-07-20
which version of ubuntu?
it may be necessary to add the xswap ppa
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

---

### Post by wildmanne39 on 2011-07-21
Hi, yes that is just a bug and you do not need to worry about that.

---

