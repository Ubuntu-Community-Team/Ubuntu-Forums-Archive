---
title: "help downloading ubuntu 10.10 with windows"
date: 2011-03-10
forum: General Help
---

### Post by zirgut on 2011-03-10
Hi,
I am struggling with downloading ubuntu 10.10 on to computer. I want to keep my windows 7 operational. I have downloaded ubuntu onto a CD. I have partitioned my C drive to install. Has 61GB space free. I expected a box to come up when installing that allowed me to install along side windows but none did. Only 2 options available, one to use whole disk space which I presumed would erase windows or 2, to do it manually (advanced) dreaded words for me!. What am I doing wrong? or what do I need to do. Also have just joined this site and have to say took me a while to work out how to post a message. Maybe some simple box to point new users to gat quick answers to their problems?:confused:

---

### Post by Rubi1200 on 2011-03-10
Hi and welcome to the forums :-)

Boot the computer with the LiveCD choosing to try not install.

At the live desktop, go to Applications > Accessories > Terminal and post the output of the following command:

```
sudo fdisk -lu
```

---

### Post by keanu-x on 2011-03-10
open the cd in windows and install it inside windows so you can have a dual boot...

---

### Post by zirgut on 2011-03-10
> **keanu-x said:**
> open the cd in windows and install it inside windows so you can have a dual boot...
Hi Thanks for that it did the trick

---

### Post by ~Plue on 2011-03-10
> **zirgut said:**
> Hi Thanks for that it did the trick
keep in mind that a wubi install is for 'trying it out' and not for long term use

---

### Post by zirgut on 2011-03-10
Many thanks for your support. On steep learning curve. I installed in Windows and all is working.

---

