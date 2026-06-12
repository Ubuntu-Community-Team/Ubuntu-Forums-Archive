---
title: "Rewriting bootloader"
date: 2011-09-14
forum: General Help
---

### Post by wilsonsamm on 2011-09-14
I was quite impressed with Ubuntu's latest LTS version (10.04) (on /dev/sda1), so I decided to try out the latest version (11.something) (I always have a spare partition, /dev/sda2, for me to try operating systems out)

But, when I put Ubuntu 11.04 up, my bootloader was overwitten! Now I can dual-boot to two variants of Ubuntu, but I am windering what'll happen when I next format /dev/sda2. I think it'll make my system unbootable, unless I rewrite the Grub that came with Ubuntu 10.04 LTS (on /dev/sda1) -- How do I do that?

---

### Post by Arand on 2011-09-14
From the LTS version use```
grub-install [OPTION] install_device
```as documented in grub-install(8).

For example, in your case this would most likely be```
sudo grub-install /dev/sda
```which will pick up the grub files it find under /boot/grub (which if you run from LTS will be the LTS boot files located on sda1), and make the main bootloader load these instead of the ones on sda2.

You may also want to re-run```
sudo update-grub
```which should, if not already done, make the LTS version of the bootloader pick up the other version and be able to boot that as well.


- arand

---

### Post by wilsonsamm on 2011-09-14
Oh that's interesting. 
Does update-grub also pick up non-debian operating systems (I have Arch Linux in mind, also Haiku)

---

### Post by Quackers on 2011-09-14
Yes it does.
In your case you need to boot into your sda1 installation and run sudo grub-install /dev/sda, as Arand said.
This will put that system in control of grub. You can then do what you want with your /dev/sda2 partition/system.

---

