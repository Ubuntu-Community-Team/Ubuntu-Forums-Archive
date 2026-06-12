---
title: "Ubuntu hard drive clone to image problem"
date: 2010-07-25
forum: General Help
---

### Post by skyhigh79 on 2010-07-25
Hi I am new to ubuntuforums and I need some help abot the problem of creating disk image of ubuntu and saving it on an external hard disk.

Below are the processes I am planning to take:

1.) Insert Linux CD and boot from it.
2.) Execute this command: dd if=/dev/sda of=/dev/sdb/disk1.img

Assuming /dev/sda is the linux hard disk and /dev/sdb/ is the external hard drive.

Situation:
1.) The external hard drive contains other important files.
2.) The external hard drive is connected using USB port to PC.
3.) the linux hard drive is a dedicated drive to linux (no windows installed in it)

Question:
1.) Would the dd command overwrite the existing/entire contents of external hard drive and replace it with the linux hard drive image?
2.) is my command correct about creating a disk image of linux? 
dd if=/dev/sda of=/dev/sdb/disk1.img 
3.) My current ubuntu installed in the disk is using Koala karmic ubuntu 9.10 , is it ok to use the latest Ubuntu CD to create a clone (for example Ubuntu 10.04 lts) and then run the dd command?

Any tip and suggestions from those familiar with this process are welcome.Thanks.

---

