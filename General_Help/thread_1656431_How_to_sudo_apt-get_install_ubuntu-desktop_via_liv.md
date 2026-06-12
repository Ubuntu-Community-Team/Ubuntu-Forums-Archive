---
title: "How to sudo apt-get install ubuntu-desktop via live cd???"
date: 2010-12-30
forum: General Help
---

### Post by maizuddin35 on 2010-12-30
Hello friends, ubuntu users ! 

I need help, I need to know, how to install ubuntu-desktop via a live cd and install it in my current problem cannot-login-ubuntu. 
check this thread from me, about the problem I have
[http://ubuntuforums.org/showthread.php?t=1654368]("http://ubuntuforums.org/showthread.php?t=1654368")

is anyone outside there know how to do it, cause I don't want to reinstall back my system.

---

### Post by b0b138 on 2010-12-30
mount the partition of your install. Either mount it via command line if you know how, or just go up to places and select it there. If you do the later, it should mount to /media/a whole bunch of numbers and letters (for example, /media/123xyz)

then run ```
chroot /media/123xyz
```
then ```
apt-get install ubuntu-desktop
```
then reboot (and cross fingers lol)

---

### Post by garvinrick4 on 2010-12-30
You have to chroot into your install in Live CD. (chroot means to be in root of file system)
I will use sda5 for this you change to what yours is. 
```
sudo fdisk -l
``` (will tell you your sda#)lower case L
Now in Live CD with internet connection:
                      ```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
apt-get install ubuntu-desktop
``````
exit
```                        ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```Reboot into Ubuntu install on HDD.

---

### Post by maizuddin35 on 2010-12-31
thank you for the reply yaw given, I'm not at my ubuntu desktop right now, and I will try this as soon I get to it. I hope it'll work

---

### Post by maizuddin35 on 2011-01-02
I've done it, It work .!thanks to @garvinrick4 for the help, and everyone else. the problem is solved

---

