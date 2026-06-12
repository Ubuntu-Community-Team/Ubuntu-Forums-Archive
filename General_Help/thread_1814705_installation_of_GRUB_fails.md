---
title: "installation of GRUB fails"
date: 2011-07-29
forum: General Help
---

### Post by chedderslam on 2011-07-29
Installing to encrypted LVM on hardware RAID array.


When it asks where to install GRUB, it defaults to /dev/mapper

I have tried /dev/mapper, /dev/boot, /dev/sda1, /boot.

raid array with:
[LIST]
[*]boot
[*]encrypted lvm
[LIST]
[*]swap
[*]home
[/LIST]
[/LIST]

I am not sure what to put there.

---

### Post by dcstar on 2011-07-30
> **chedderslam said:**
> Installing to encrypted LVM on hardware RAID array.


When it asks where to install GRUB, it defaults to /dev/mapper

I have tried /dev/mapper, /dev/boot, /dev/sda1, /boot.

raid array with:
[LIST]
[*]boot
[*]encrypted lvm
[LIST]
[*]swap
[*]home
[/LIST]
[/LIST]

I am not sure what to put there.

Try /dev/sda (assuming your boot drive is /dev/sda)

---

