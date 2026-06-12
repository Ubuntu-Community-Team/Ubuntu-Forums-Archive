---
title: "CLI command to get usb device names"
date: 2009-07-13
forum: General Help
---

### Post by RadarBat on 2009-07-13
What command do you use to find out what the usb devices' names are that are connected to the PC?

---

### Post by x33a on 2009-07-13
try
```
lsusb
```

---

### Post by RadarBat on 2009-07-14
> **x33a said:**
> try
```
lsusb
```

Thank you, but I need to know the "/dev/sda" or "/dev/sdb1", and the size of the /dev so I can tell what's what when I have more than one flash drive/SDHC card plugged in to the PC.   RB

---

### Post by fragos on 2009-07-14
The 1st one will mount as /media/disk and the next as /media/disk-1.

---

