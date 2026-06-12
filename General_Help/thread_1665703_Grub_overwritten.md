---
title: "Grub overwritten"
date: 2011-01-12
forum: General Help
---

### Post by Aztek on 2011-01-12
I have a 120GB hard drive partitioned approximately as follows:

512MB ext2 (primary): /boot
30GB ntfs (primary) : Windows 7
20GB ext4 (logical) : Ubuntu 10.10
20GB ext4 (logical) : Ubuntu 11.04 alpha
40GB ext4 (logical) : empty
2GB                 : swap

I installed in the following order:

Windows 7 > 10.10 > 11.04

I told 10.10 to mount /boot to the boot partition, while I told 11.04 to simply installed everything to its own partition. I wanted the grub from 10.10 to control everything at boot, but when I installed 11.04 its grub took control. 

Why did this happen and how can I fix it?

Thanks

---

### Post by oldfred on 2011-01-12
If your grub from 11.04 lets you boot your 10.10 install, just reinstall grub from that. You do not have to use LiveCD.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

When you install, you have to use manual install to get the chooser on where to install grub2 and I did not see a do not install choice. Just about every other distribution lets you always choose where to install or whether to install the boot loader.

---

