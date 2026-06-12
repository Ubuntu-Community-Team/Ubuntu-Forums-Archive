---
title: "dual boot"
date: 2010-02-16
forum: General Help
---

### Post by earlyon on 2010-02-16
I had installed ubuntu (9.10) on a DELL Inspiron 600. It was working great. A tax application required windoz. I created a new partition. And without saving grub, intalled xp professional. Now it only boots to xp.

Used ubuntu live cd, and was did not see any grub files on /boot/grub.

I have read the post on Howto: RESTORGRUB (if your MBR is messed up). But I am not sure if is applicable.

Thank you in advance for any suggestions and help.
- earlyon

---

### Post by Locutus_of_Borg on 2010-02-16
its been a while since i used grub, but from the live cd, mount your linux / partition to /mnt then chroot into it with:

sudo chroot /mnt/ /bin/bash

then issue:

grub-install /dev/sda

else this: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by 2hot6ft2 on 2010-02-16
Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
```
Then to find out your partitions with
```
fdisk -l
```
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```

From the [Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275")

---

