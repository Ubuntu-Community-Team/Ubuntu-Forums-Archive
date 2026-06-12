---
title: "grub needs moved"
date: 2010-06-19
forum: General Help
---

### Post by dave_man137 on 2010-06-19
I was installing fedora 13 just for fun and it move grub boot to different partition. Now I can't boot anything but fedora I know I need to be booting from hd0 sa1 but grub loads from hd0 sa7 Please help I just need my ubuntu os back thanks

---

### Post by oldfred on 2010-06-19
Be sure to reinstall the same version of grub or grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by garvinrick4 on 2010-06-19
> **dave_man137 said:**
> I was installing fedora 13 just for fun and it move grub boot to different partition. Now I can't boot anything but fedora I know I need to be booting from hd0 sa1 but grub loads from hd0 sa7 Please help I just need my ubuntu os back thanks
Put in live CD, your install CD and choose try Ubuntu. When it boots up go into gparted right click on your sda install choose sda1 (that you say is your Ubuntu install) and choose
label. Now label your partition to whatever you want I am going to use lucid for this, make sure you click green apply arrow on top to apply label. And sda1 for your partition with Ubuntu. Change either one if different. Now open a terminal and use these commands.

```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda1 /media/lucid
```                          ```
sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda") 
``````
sudo umount /media/lucid
``` (not a typo)

You are making a directory for lucid install
you are mounting the drive
you are putting grub in sda's in mbr. Not sda1 or sda5 but always sda
you are unmounting lucid and umount is right command
after labeling lucid mount point is now /media/lucid
I find it easier to use labels on partitions for learning purposes when over 1 install.

Take out CD and boot into Ubuntu and run.

sudo update-grub

sudo grub-mkconfig

Done.

---

