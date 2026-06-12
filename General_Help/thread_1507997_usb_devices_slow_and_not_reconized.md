---
title: "usb devices slow and not reconized"
date: 2010-06-12
forum: General Help
---

### Post by 91corradotdi on 2010-06-12
hello I upgraded to 10.04 LTS and noticed that my usb sd card reader was real slow and sometimes could not even load a photo. I installed the latest update  and then it would not recognize my usb hard drive or my card reader. I restarted it still the same. the next day I restarted it and they reappeared but very slow to read anything from them.

---

### Post by dino99 on 2010-06-12
pmount and usbmont have to be installed ( check with synaptic)

sudo update-pciids && update-usbids

---

### Post by 91corradotdi on 2010-06-12
installed pmount and usb mount restarted the computer no change. the card reader is soooo slow to view photos. it was not like this at all on the older version of ubuntu. I checked the info on the card reader with disk utility and it reads usb at 480 mbs. partition type fat 16 (0x06)
I also tried to benchmark and this is what I got
Error benchmarking: helper exited with exit code 1: Error reading 104857600 bytes at 104857600 from /dev/sdb when guesstimating buffer size: Input/output error

---

