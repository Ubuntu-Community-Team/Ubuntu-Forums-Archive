---
title: "a problem with the launch in ubuntu 10.10"
date: 2010-09-20
forum: General Help
---

### Post by to6eto on 2010-09-20
problem is the following
[http://img831.imageshack.us/img831/8327/image0582.jpg](http://img831.imageshack.us/img831/8327/image0582.jpg)
to go to to give him loads of ...
[http://img651.imageshack.us/img651/9692/image0583.jpg](http://img651.imageshack.us/img651/9692/image0583.jpg)
ubuntu installed on a share of hdd samsung 
I had ubuntu 10.04 and I had no problems, GRUB starts

---

### Post by searchfgold6789 on 2010-09-20
Boot to any live CD
```
sudo mount /dev/sdXX /mnt 
sudo mount --bind /dev  /mnt/dev 
sudo mount --bind /dev/pts  /mnt/dev/pts 
sudo mount --bind /proc /mnt/proc 
sudo mount --bind /sys  /mnt/sys 
sudo chroot /mnt
sudo update-grub
```

---

