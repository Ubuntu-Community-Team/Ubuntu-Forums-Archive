---
title: "i can't change partition size with Gpated"
date: 2011-05-10
forum: General Help
---

### Post by chuchi on 2011-05-10
Hi friends!! I want to resize a partition with gparted but i can't. This is what Gparted shows:

1º 60 GB free.

2º /dev/sda5 ext3 (wifiway) 9 GB

3º /dev/sda6 linux-swap 1.30 GB

4 º /dev/sda3 ext4 (ubuntu) 31 GB

5º /dev/sda4

So i want to allocate the 60 GB to  /dev/sda5 (wifiway), and then reallocate to /dev/sda3, because I've been told that you can't allocate the 60 Gb directly to /dev/sda3, because you only can allocate space between  together partitions.
I have attached a picture of Gparted.

Thank you very much!!

---

### Post by TeoBigusGeekus on 2011-05-10
You have to resize the extended partition, ie. /dev/sda2.

---

### Post by mikewhatever on 2011-05-10
Why do you want to add 60GB to /sda5? If it's the boot partition, then it's already too large as is. How do you plan to use the added space? Furthermore, the free space and sda5 are in no way together. Sda5 is a logical partition and the unallocated space it outside the extended partition (sda2).
Last but not least, why can't you resize partitions? Does the mouse get stuck or the screen go blank?

---

