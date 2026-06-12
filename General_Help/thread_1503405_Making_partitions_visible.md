---
title: "Making partitions visible"
date: 2010-06-06
forum: General Help
---

### Post by cherithbrook on 2010-06-06
I have installed on my harddrive 3 partitions plus swap.I have sda1, sda3, sda4. I upgraded sda3 on Ubuntu 9.10 to 10.04. However on reboot sda1 and sda4 are missing. I have updated the grub but still cannot access them. They are all present on fdisk. How do I retrieve these invisible partitions please.

---

### Post by whiteychs on 2010-06-06
Check your /etc/fstab and make sure it's correct.

You can try mounting them manually.
sudo mkdir /media/HDP_1
sudo mount /dev/sda1 /media/HDP_1

---

