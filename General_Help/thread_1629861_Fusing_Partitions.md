---
title: "Fusing Partitions"
date: 2010-11-24
forum: General Help
---

### Post by Haedrian on 2010-11-24
I currently have a system which dual-boots another OS on one Partition and Ubuntu on another. Now I was considering removing the other partition - since I don't need it anymore, and I could use the extra space for Ubuntu.

Is there a way for me to do this WITHOUT having to clear both partitions and install everything from scratch? Or at least, removing the other OS from the partition (and GRUB) and recovering space that way?

Thank you.

---

### Post by matt_symes on 2010-11-24
Hi

First backup your existing drive in case something goes wrong.

Boot into the LiveCD and use GParted to remove the partition you want to remove and resize the partition you want to resize.

Kind regards.

---

