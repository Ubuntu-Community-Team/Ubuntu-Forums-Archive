---
title: "Add Live USB as Software Source"
date: 2010-07-18
forum: General Help
---

### Post by timbalisto on 2010-07-18
I don't have an active Internet connection at home, so I use my neighbor's computer with my live usb Lucid Lynx and install packages on it (the live usb). Can I take my live usb home and use it as a software source on my desktop to install the packages that I installed on the live usb? If I have to manually type in the source, what would be the syntax of the flash drive?

---

### Post by timbalisto on 2010-07-25
::Bump::

---

### Post by timbalisto on 2010-07-29
Is there no way to do this?

---

### Post by sikander3786 on 2010-07-29
> **timbalisto said:**
> I don't have an active Internet connection at home, so I use my neighbor's computer with my live usb Lucid Lynx and install packages on it (the live usb). Can I take my live usb home and use it as a software source on my desktop to install the packages that I installed on the live usb? If I have to manually type in the source, what would be the syntax of the flash drive?

Hi.

Through Live USB it might be possible by installing the packages, then there is a software called APTonCD. That will burn the selected packages on to the CD-ROM for backup and future install. Take a look at APTonCD. I am sure that will help you.

What I used to do when I didn't have an active internet connection at home, I downloaded the packages from packages.ubuntu.com, and all of their dependencies. Note only dependencies of the software, not the dependencies of the dependencies. (I hope you get it). Then install them on my home PC by installing the dependencies first and then the actual software package.

GDEBI tells you if any dependencies are unsolved and you might go again to the neighbours PC and download those packages.

Offline software installation is  always a hassle on most Linux Distros.

HTH.

---

### Post by timbalisto on 2010-07-30
Thank you so much!

---

