---
title: "Flash memory problems"
date: 2012-02-05
forum: General Help
---

### Post by Historynut on 2012-02-05
I have a one gig flash drive that I want to use to transfer info between my two computers. The notebook sees it and will read from and write to it. The PC sees it, will read from it but will not write to it, telling me that it doesn't exist. How do I make the PC write to the flash memory? The notebook is Ubuntu 7.x, the PC is the latest Ubuntu.

---

### Post by SteveDee on 2012-02-06
> **Historynut said:**
> ... How do I make the PC write to the flash memory?...

In the absence of any other suggestions, I'd suggest you save the data from the memory device, then run GParted to re-format the device.

Use a format that will be supported by 'buntu 7.xx and 11.xx (or FAT32 which will also be OK on Windows).

---

