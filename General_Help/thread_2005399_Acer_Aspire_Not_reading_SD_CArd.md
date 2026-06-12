---
title: "Acer Aspire Not reading SD CArd"
date: 2012-06-17
forum: General Help
---

### Post by groeswenphil on 2012-06-17
Hi group,

Just loaded Lubuntu onto my Acer Aspire 1 Netbook. All working well but it can't see my SD card. The Acer Aspire One has an SD card reader fitted as standard. It isn't being seen. I guess I need some terminal trickery?

All the best,
Phil

---

### Post by Autodave on 2012-06-17
> **groeswenphil said:**
> Hi group,

Just loaded Lubuntu onto my Acer Aspire 1 Netbook. All working well but it can't see my SD card. The Acer Aspire One has an SD card reader fitted as standard. It isn't being seen. I guess I need some terminal trickery?

All the best,
Phil

Was the card in the machine when you did the install?

---

### Post by wilee-nilee on 2012-06-17
My own aspireone d250 is a bit temperamental with the SDHC Class 10 card I have..

Sometimes it is a reboot to get it to show sometimes just unplugging and plugging in, maybe even several times.

Formatting it with gparted may help.

You could run this to see if it shows.
```
sudo fdisk -l 
```

---

