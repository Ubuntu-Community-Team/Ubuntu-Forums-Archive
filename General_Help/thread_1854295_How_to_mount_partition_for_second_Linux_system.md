---
title: "How to mount partition for second Linux system?"
date: 2011-10-04
forum: General Help
---

### Post by KonfuseKitty on 2011-10-04
My hard drive is partitioned:

sda1 - ext4 - mounted as '/'

sda2 - swap

sda3 - ext4 - mounted as '/home'

sda4 - ext4

The last partition, sda4, I would like to use to install another Linux system, either another Ubuntu version or a different distro. I'm just not sure how to do that... Do I mount it as '/' also? Will that not cause confusion at startup?Apologies for such a basic question, but I haven't been able to find an answer. (Everything I found is geared toward dual Win/Linux installations.)

---

### Post by dcstar on 2011-10-04
> **KonfuseKitty said:**
> My hard drive is partitioned:

sda1 - ext4 - mounted as '/'

sda2 - swap

sda3 - ext4 - mounted as '/home'

sda4 - ext4

The last partition, sda4, **I would like to use to install another Linux system,** either another Ubuntu version or a different distro. I'm just not sure how to do that... Do I mount it as '/' also? Will that not cause confusion at startup?Apologies for such a basic question, but I haven't been able to find an answer. (Everything I found is geared toward dual Win/Linux installations.)

You don't use existing partitions, delete it so the install has free space.

---

### Post by garvinrick4 on 2011-10-04
Yes at install mount point is / and at grub menu entry screen will give you a list
to choose which installl you want to boot. When you decide what you would like
to install as another distro post back here some will use same /home others are
a pain to use same /home. Some use grub2 and some use grub-legacy and they
do not play together well. So post will let you know the best way to install.
```
sudo fdisk -l
```
Lower case L
```
sudo parted -l
```
Lower case L

Post output of these to also just copy and paste from the terminal.

---

### Post by KonfuseKitty on 2011-10-04
The other distro would be Debian, which I guess should work as explained. I'll try anyhow. Marking this as solved - thanks.

---

