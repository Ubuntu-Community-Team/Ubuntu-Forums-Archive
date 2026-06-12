---
title: "Dual boot xp/mint linux - how do i replace mint with ubuntu 10.4"
date: 2010-10-19
forum: General Help
---

### Post by sabreranger on 2010-10-19
Hi I am successfully running ubuntu 10.4/vista dual boot on one of my laptops. I have another laptop running xp media/ Mint linux. I want to replace the mint for ubuntu 10.4, any ideas which is the easiest way to do this....

---

### Post by macem29 on 2010-10-19
install ubuntu to the partition where mint lives

---

### Post by sabreranger on 2010-10-19
Do you know what the settings are as there are a couple of drop down boxes with various details

---

### Post by sabreranger on 2010-10-19
This is where i get stuck on the manual partition settings, when I change the mint are i get an error message which says no root drive.

---

### Post by sikander3786 on 2010-10-19
For the easiest way, you can select manual partitioning from Ubuntu installer and then choose your Mint partition's mount point as '/' for Ubuntu and mark it for a format.

You can leave your previous Swap partition as it was and Ubuntu will happily pick it up.

Let Grub install as it does by default and you'll be dual booting Windows.

If you are unsure, please post the output of

```
sudo fdisk -l
```

from Mint or and Ubuntu live CD so we can have a look at your partitions.

---

