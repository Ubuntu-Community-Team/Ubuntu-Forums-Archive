---
title: "Ubuntu/Kubuntu Dual boot"
date: 2010-07-24
forum: General Help
---

### Post by su-37 on 2010-07-24
Hey ive dual booted Kubuntu and Ubuntu (ubuntu installed first) and i was wondering how to get rid of Kubuntu without killing Ubuntu?

---

### Post by oldfred on 2010-07-24
You need to reinstall Ubuntu's boot loader to the MBR, boot into Ubuntu and install grub2 to the MBR:

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

Then you can delete your other install. After deleting you will need to run the sudo update-grub again so it does not see it.

---

