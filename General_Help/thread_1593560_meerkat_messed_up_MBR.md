---
title: "meerkat messed up MBR"
date: 2010-10-11
forum: General Help
---

### Post by utnubuuser on 2010-10-11
Hello
Decided to try Meerkat. Looks great from the USB.  With Lucid installed on Dell Optiplex with Windows XP - worked out ok.

Installed Maverick Meerkat from USB and now no OS at all. I only get a prompt to re-try booting or to enter set-up.

I installed Meerkat to the existing Lucid partitions, a / and /home partition, but I'm not even getting as far as grub-menu at boot.

In the first attempt the installer installed grub to sda, (the hdd), and that didn't work, so I tried re-installing with a separate /boot, (sda7), partition, and still no love.

One of the problems is that on the Dell there is a /dell utility partition at the beginning of the disk, so I can't really move that to put a /boot partition at the beginning.

Oddly, Lucid had no such problem.  Lucid installed and recognised Windows XP, but when I try the same install procedure with Meerkat I draw a blank.

Any suggestions as to what I might try are welcome - it's a new install and my /home is seperate. 

Basically, how to deal with grub not happening. Is there a way to install just Grub2, and where to.  Almost all the grub how-tos are for legacy grub

---

### Post by utnubuuser on 2010-10-12
This problem was caused by the USB-Flash drive.  As soon as the flash-drive was removed, the problem disappeared.

---

