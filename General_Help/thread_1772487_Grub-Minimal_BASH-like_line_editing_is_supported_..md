---
title: "Grub-Minimal BASH-like line editing is supported ..."
date: 2011-05-31
forum: General Help
---

### Post by newbie2010 on 2011-05-31
Hi,

I had a dual boot with Ubuntu 11.04 and Windows vista. Upon  upgrading to windows 7, i found my grub to be replaced, with windows  boot loader. So i booted from a live USB with Ubuntu 11.04 and followed  steps as follows.

1. Mounted the partition where i have ubuntu 11.04
2. mount | tail -1
3. sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda
4. Reboot

On rebooting, I find grub to open in terminal mode, and does not allow me to log in either in windows or in Ubuntu! Please help!

All  i get is a grub terminal [ Minimal bash-like editing is supported. For  the first word, TAB lists possible completions of a device/filename. ]

Please help!!

---

### Post by TeoBigusGeekus on 2011-06-01
See [this]("https://help.ubuntu.com/community/Grub2#METHOD 3 - CHROOT").

---

