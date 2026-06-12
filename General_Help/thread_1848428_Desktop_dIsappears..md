---
title: "Desktop dIsappears."
date: 2011-09-22
forum: General Help
---

### Post by backspace on 2011-09-22
Hi, I really need some help here. So far I've tried almost everything.
This is about my 5th or 6th fresh install, from 9.04, 10.04, 10.10 and 11.04.; always ending in the desktop disappearing, leaving just the wallpaper and mounted drive icons.

I've been using Ubuntu for years and this is the first really big disappointment that I have experienced. Always with the same machine and same graphic card/drivers (Nvidia Geforce4  MX 440).

I downloaded the recommended Nvidia driver from Nvidia, and installed per the guide.

1. Go to NVIDIA website and download the compatible driver for your graphic card series.
2. Reboot your Ubuntu.
3. Choose the ‘Recovery Mode’ on GRUB.
4. Go to the bottom of menu list, choose ‘root console’.
5. Disable the Kernel Nouveau.
#echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
#update-initramfs -u
Reboot.
6. Change to init 3
#init 3
7. Install the NVIDIA driver
#sudo sh NVIDIA-XXXXXX.run
8. Reboot your Ubuntu.

Each time, things last up to the first reboot.

I don't get a problem if I log in using Gnome "Safe Mode". . . the desk top is still there.

I would really appreciate any help on this one.

Regards Paul

---

