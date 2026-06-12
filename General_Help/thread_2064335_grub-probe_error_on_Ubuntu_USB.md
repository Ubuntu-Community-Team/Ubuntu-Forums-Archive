---
title: "grub-probe error on Ubuntu USB"
date: 2012-09-29
forum: General Help
---

### Post by AmateurDev on 2012-09-29
I am running Ubuntu 12.04 from a persistent USB drive. I am trying to set up Grub to boot automatically, but I need to generate a grub.cfg file. For some reason, update-grub and grub-mkconfig fail because of grub probe:
```
sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is dev mounted?).

```
I figured it had to do with my OS ISO being on a different partition (/dev/sda2) than the partition with Grub installed, but I don't know how to redirect the script. I can get grub-probe to succed if I run:
```
sudo grub-probe -d /dev/sda1
fat
```
However, I can't modify the path from update-grub or grub-mkconfig. Thanks for your help!

---

