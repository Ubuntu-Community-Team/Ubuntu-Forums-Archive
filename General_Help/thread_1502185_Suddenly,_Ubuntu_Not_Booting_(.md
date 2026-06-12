---
title: "Suddenly, Ubuntu Not Booting :("
date: 2010-06-05
forum: General Help
---

### Post by aatkco on 2010-06-05
Hi Linux users,

My Lucid Installation was working like a charm until I installed a new grub splash image using terminal command provided by ubuntu geek from this url :
[http://www.ubuntugeek.com/grub2-splash-images-for-ubuntu-10-049-10.html](http://www.ubuntugeek.com/grub2-splash-images-for-ubuntu-10-049-10.html)

When I restarted after finishing my work and tried to boot into ubuntu again ( Using another bootloader called Chameleon ) , Grub didn't show and There is a non-stop sound coming from the cpu , I inserted the 9.10 live cd and installed grub2 again but it installed to the mbr ( the whole disk ) and now it controls the multi booting process, But the system booted fine, I reinstalled Chameleon and i just need to install grub to dev/sda6 and not the whole mbr. 
Thanks

---

### Post by Barafu Albino Cheetah on 2010-06-05
First, name you thread to relate to your question. 
Second. "How to install grub2 on selected partition. would suffice, we don't care that you know what Chameleon Is. 
Third, run the following
```
sudo update-grub
sudo grub-install /dev/sda6
```

---

### Post by aatkco on 2010-06-05
> **Barafu Albino Cheetah said:**
> First, name you thread to relate to your question. 
Second. "How to install grub2 on selected partition. would suffice, we don't care that you know what Chameleon Is. 
Third, run the following
```
sudo update-grub
sudo grub-install /dev/sda6
```
sudo grub-install /dev/sda6 
Could not find device for /boot: Not found or not a block device.

---

### Post by dino99 on 2010-06-05
before to play like a geek, better to know the basic commands and be able to understand what you are doing :confused:

how many bootloaders do you need ? If you do silly things, no need whining

boot without "splash" on the boot line, then remove your crap

---

### Post by oldfred on 2010-06-05
Barafu Albino Cheetah's command should work from your install or did you run it from the liveCD which requires different command.

It will probably come back with a warning and say blocklists are unreliable and if you really want to re unreliable you have to add --force to the command.

Install from LiveCD:
Find linux partition change sda5 if not correct or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub


I do not remember if this gives a choice of partitions as well as drives
run from working system

sudo dpkg-reconfigure grub-pc

---

