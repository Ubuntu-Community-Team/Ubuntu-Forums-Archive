---
title: "usb wrong size - partition table error"
date: 2012-05-07
forum: General Help
---

### Post by LorenzoApps com on 2012-05-07
Hi, I just installed the last version of Ubuntu (12.04) and, while I was working with a usb pen drive, I had a problem. 

First time I used it - the system correctly found it was 8 GB.
Second time - I used it went down to 8 MB.

Guess it was the partition table and I changed the values using fdisk and sfdisk, but nothing seemed to work,
sudo fdisk -C 1023 -H 249 -S 62 /dev/sdb

Can you help me?

---

