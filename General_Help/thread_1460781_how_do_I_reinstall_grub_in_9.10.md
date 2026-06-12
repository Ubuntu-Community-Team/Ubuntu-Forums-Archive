---
title: "how do I reinstall grub in 9.10"
date: 2010-04-23
forum: General Help
---

### Post by Hyper Tails on 2010-04-23
Hi I have 7 And Karmic and I recently a 1080p monitor, new graphics card and 8 gbs of ram, I reinstalled 7 (using 64-bits per pixel instead) and I tried reinstalling the grub menu in the live usb and it doesn't work like it did back in earlyer versions of ubuntu

thank you

---

### Post by oxf on 2010-04-23
See here
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
:)

---

### Post by Hyper Tails on 2010-04-23
Tried It and Didn't work

I keep getting error messeges

like can find this and that or example

---

### Post by 2hot6ft2 on 2010-04-23
Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
```
To find out you partitions run
```
fdisk -l
```
Use that info for the following
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
You'll want to install grub to the drive that is first in the boot order in the BIOS
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process and once you're back in ubuntu run
```
sudo update-grub
```

---

### Post by Hyper Tails on 2010-04-23
Thank you!!!

got it working!

I really appericated your help 

so again Thank you

---

