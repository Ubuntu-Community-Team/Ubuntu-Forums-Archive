---
title: "USB Drive not recognized"
date: 2010-02-04
forum: General Help
---

### Post by Living_The_Dream on 2010-02-04
I am having a problem with one of my USB drives not being recognized in Ubuntu 9.10. It used to recognize it but them one day it stopped (I don't use my drive very often on this particular computer so I don't remember what I may have installed or changed). It will still recognize my other USB drive, one i formatted to be a boot drive in Ubuntu. If you need anymore info please let me know and I'll post it as soon as I can.

---

### Post by audiomick on 2010-02-04
First thing to do is plug it in and then open a terminal and do
```
lsusb
```
The drive should be visible in the output, as far as I know. If it is not, that might indicate that the drive itself has a problem, or maybe a bad cable.

---

### Post by Leppie on 2010-02-04
you say that you don't use that drive very often on this particular pc, does it work on other pc's?

---

### Post by Living_The_Dream on 2010-02-06
> **Leppie said:**
> you say that you don't use that drive very often on this particular pc, does it work on other pc's?
It works fine on my home PC. I dual boot Windows 7 and Ubuntu and it is recognised right away on both. It's only on my work computer that it is not recognised.

---

### Post by Leppie on 2010-02-06
have you checked the logs after connecting the usb drive?
something like this:
```
dmesg | tail
```

---

### Post by Living_The_Dream on 2010-02-17
Problem solved. Lost my flash drive.

---

