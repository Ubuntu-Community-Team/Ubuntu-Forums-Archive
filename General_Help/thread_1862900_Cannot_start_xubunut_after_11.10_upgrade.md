---
title: "Cannot start xubunut after 11.10 upgrade"
date: 2011-10-17
forum: General Help
---

### Post by mixmaster on 2011-10-17
I have just run the online upgrade on a Xubuntu 11.04 system.

The upgrade appeared to work ok but now I get the grub menu, select the default option and get an error

hd2 write error

followed my a mount error which flashes past too quickly to read and then I end up in the busybox shell.

I can reinstall from scratch if I have to but I would like to know what has happened for fear it might happen again when the machine has more valuable data on it.

---

### Post by marinara on 2011-10-20
i had a similar problem, was getting a black screen on boot up

---

### Post by scania_gti on 2011-10-22
For me work:```
sudo apt-get install kdm
```
or ```
 sudo dpkg-reconfigure kdm
```

---

### Post by 2F4U on 2011-10-22
Can you check the hdd for errors in the busybox shell, for example

fsck /dev/sda1

if /dev/sda1 is your root partition.

---

