---
title: "no space left!"
date: 2011-06-21
forum: General Help
---

### Post by linuxiano on 2011-06-21
Hello

I installed ubuntu 10.04 beside xp ,it worked fine at beginning then i have this problem:
it says no space left but it's not true  ,I googled it found some topics but none helped me

btw this my first week using linux os,any help is appreciated

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            2.7G  2.6G     0 100% /
none                  874M  656K  873M   1% /dev
none                  880M   24K  880M   1% /dev/shm
none                  880M   96K  880M   1% /var/run
none                  880M     0  880M   0% /var/lock
/dev/sda6             9.1G  4.3G  4.8G  47% /host
/dev/sda1              18G   16G  1.7G  91% /media/96BCB543BCB51EA5
/dev/sda5              12G  5.3G  6.5G  45% /media/FC1482B214826F86

```

---

### Post by WorMzy on 2011-06-21
You haven't installed beside XP, you've installed Ubuntu *inside* XP as Wubi. You chose to set aside 2.7GB of space for Wubi's disk, and this is now almost completely full. See this wiki for advice on how to proceed from here: [https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

---

### Post by haqking on 2011-06-21
You have installed in XP not next to it using Wubi

EDIT: WorMzy beat me to it ;-)

---

### Post by linuxiano on 2011-06-22
thanks for replies, i resized my disk but again it's full ,i think the problem is from "/dev/loop0" what is that? and how to fix it?

---

### Post by wildmanne39 on 2011-06-22
Hi, WorMzy gave you a link to resize that drive to make it bigger that is the answer, and the loop0 is where ubunbtu is installed through windows.

---

