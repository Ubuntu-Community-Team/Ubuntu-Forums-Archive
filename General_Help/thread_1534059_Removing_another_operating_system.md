---
title: "Removing another operating system?"
date: 2010-07-18
forum: General Help
---

### Post by TheWeakSleep on 2010-07-18
Hey guys, I installed crunchbang linux last night as a dual boot with ubuntu, and it's just not for me right now :D I tried to delete the partition or whatever, though when I turned the computer back on, it tried to open up grub or something like that :D I ended up reinstalling it to get to my ubuntu partition, but I would still like to remove it. I guess what I'm asking is how can i remove crunchbang while still being able to get into my system?

Thanks in advance

---

### Post by oldfred on 2010-07-19
If you can boot into Ubuntu reinstall grub2 from there, if not you need the Ubuntu liveCD to reinstall grub2. Ubuntu's grub2 has to be in the MBR to boot Ubuntu and it sounds like you have crunchbang's grub in the MBR.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by TheWeakSleep on 2010-07-19
worked perfectly:) thanks for your quick help!

---

