---
title: "Ubuntu 11.10 stop booting"
date: 2012-01-19
forum: General Help
---

### Post by gertjuhh on 2012-01-19
I tried turning on my computer today but was welcomed by a nice black screen pointing out that I don't have any devices to boot from.
So i plugged in my ubuntu USB-stick, which I also used to install the system, and started gparted.

GParted
[IMG]http://img26.imageshack.us/img26/8302/screenshotat20120119195.png[/IMG]

Information screen of /dev/sda2
[IMG]http://img708.imageshack.us/img708/8302/screenshotat20120119195.png[/IMG]

Information screen of /dev/sda1
[IMG]http://img21.imageshack.us/img21/8302/screenshotat20120119195.png[/IMG]

I have no idea what /dev/sda1 is for, during install i let the installer handle partitioning the disk.
It worked fine for a few days, and now this.
I did not try to repartition, or install windows along side, or anything along those lines, prior to this problem.

Any pointers on how to solve this problem?
Much appreciated.

---

### Post by deonis on 2012-01-19
good time to move back to Ubuntu 10.04 :)

---

### Post by LinuxFan999 on 2012-01-19
The only thing you can do is reinstall Ubuntu. This time, however, you should partition the drive yourself and create a separate /home partition.

---

