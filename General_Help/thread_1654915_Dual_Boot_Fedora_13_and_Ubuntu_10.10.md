---
title: "Dual Boot Fedora 13 and Ubuntu 10.10"
date: 2010-12-29
forum: General Help
---

### Post by timzorr on 2010-12-29
i have been trying too dual boot fedora 13 and ubuntu 10.10. i have already had ubuntu 10.10 installed and i put the fedora 13 live cd in and shrank my ubuntu volume to create two different partitions. after everything installed i could only boot into fedora. no grub menu would come up**. how do i fix this ?**

---

### Post by garvinrick4 on 2010-12-29
> **timzorr said:**
> i have been trying too dual boot fedora 13 and ubuntu 10.10. i have already had ubuntu 10.10 installed and i put the fedora 13 live cd in and shrank my ubuntu volume to create two different partitions. after everything installed i could only boot into fedora. no grub menu would come up**. how do i fix this ?** You should have choosen in Fedora not to install any grub at all and then booted into Ubuntu and updated your grub to add fedora in config and bootmenu entry.
Now put in a live cd and reinstall grub2 to mbr. You now have fedora's grub legacy installed. grub-legacy and Ubuntu's grub2 do not work together well.
Get your sda number of ubuntu install I will use sda1 for this code, change to your own sda# can use sudo fdisk -l (small L)
In Live CD. Open a terminal
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```boot into Ubuntu and
```
sudo update-grub
```

---

### Post by timzorr on 2010-12-29
I have followed your instructions and i am now able to boot into ubuntu. i have ran the ```
sudo update-grub
```. Now i can't get into fedora. In my grub menu on ubuntu fedora is not showing up.:confused:

---

### Post by garvinrick4 on 2010-12-29
# Go into live Cd and chroot into fedora install and remove grub-legacy as per below: I am doing grub and grub-common: Should clean out anything installed with grub-legacy
# I have used sda6 use your own fedora sda#



```
sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
yum remove grub 
``````
yum remove grub-common
``````
exit
```                        ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``` ```
sudo reboot
```Boot into Ubuntu
```
sudo update-grub
```

---

