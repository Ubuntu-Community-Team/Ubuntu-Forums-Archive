---
title: "partitions/drives sometimes not showing"
date: 2011-05-14
forum: General Help
---

### Post by n1ght5t4lk3r on 2011-05-14
I upgraded to Ubuntu 11.04 from 10.10 about a week or so ago and since the upgrade when I boot into Ubuntu  (I am running a dual boot Ubuntu and win7) other HDD's and partitions often do not show up anywhere on my system. For example I have an ntfs partition that I store music on so I can access it on either windows or ubuntu, as well as other partitions. When this issue occurs even my dvd drive appears not to exist. I have to reboot my machine sometimes 4 or 5 times before the drives/partitions show again. I had no issue like this before running the upgrade or using earlier versions of Ubuntu.

---

### Post by dozycat on 2011-05-14
I did a dual windows 7 and ubuntu 11.04 64 bits clean installation on a machine I5 2400 motherboard ASUS H67 and I have similar problem.
I can´t see the LG dvd drive from ubuntu but I can see it from windows.

---

### Post by n1ght5t4lk3r on 2011-05-14
yeah i should also maybe have mentioned its the 64 bit version I am running also, and I just saw another thread from someone having dvd  drive issues in 64 bit also. Although its not just my dvd drive, its my HDDs and partitions too except for where I have ubuntu installed

---

### Post by dozycat on 2011-05-14
You can check with:
dmesg | grep dvd
or
dmesg | grep cd

I will try later when I will be back home.

Please include the link to the other thread.

---

### Post by dozycat on 2011-05-14
I checked and no messages about CD or DVD.

---

### Post by dozycat on 2011-05-16
Solved my problem, changing in the bios the sata  from ide to ahci. maybe it could your problem too.

---

