---
title: "HOWTO Set the correct timezone for your Persistent USB Startup Disk"
date: 2009-11-11
forum: General Help
---

### Post by dcstar on 2009-11-11
When you create a USB Startup Disk, it uses the default (US) setting on the ISO/CD that you used to create it and can be quite annoying if you actually reside in a different zone. This can be simply changed on a Persistent system by running this command:
```
sudo dpkg-reconfigure tzdata
```
Simply select your correct timezone and on the next boot things should be ok. I have tested this on a 9.10 i386 USB Startup Disk.

---

