---
title: "Noobie Screw Up..."
date: 2010-05-04
forum: General Help
---

### Post by Zionoxis on 2010-05-04
Ok, I am COMPLETELY new to Ubuntu and started with something over my head. :P
I have installed it to my desktop as a dualboot and everything worked fine. Then, I tried to follow a tutorial on how to set up my 8GB flash drive so I could boot into Ubuntu from my school computers...I started following the tutorial and got stuck.

Once I booted back into my Windows 7 OS, the flash drive now has a max capacity of 750mb... I don't think there are any other partitions. I made a few commands in Terminal in Ubuntu by following some link...

Does anyone know how I can reset it back to 8GB and how to do it correctly?

And where is a good place to start so I can learn and not completely mess up again?

Terminal Commands Used:
-Delete Partition 1
-Write Partition to 1
-Set partition to FAT 16


That is what I remember but I don't remember the commands. :P  I'm hoping someone will have some idea of what I am talking about. I feel like such an idiot.

Also, I have a Linskys wireless card in my desktop and it is to connect to my wireless network. (WEP Password protected)
Any idea how to enable it and connect?

---

### Post by Naitsirhc Hsem on 2010-05-04
I would use gparted to reformat the drive, it can be installed via ```
sudo apt-get install gparted
```  As for installing to a flash drive, I would remove all hard drives from a computer, boot from a live cd, and plug in the flash drive.  from there you can install to the flash drive as you would a hard drive

---

### Post by techunit on 2010-05-04
Alright you need to boot into a live cd and start gparted. Then select the thumbdrive in the dropdown to the top right it will update then you will be able to repartition the thumbdrive so it only has one partition. 

Here is some instructions on using gparted [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

once you have it fixed then you should head over to [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) and use the instructions to do it then.

---

### Post by itachisxeyes on 2010-05-04
ok, for the Jump Drive install Gparted and format it to FAT 32 (for the Ubuntu live USB you could just go to System>Administration>Start Up Disk Creator)

and for your wireless, with an ethernet connection, go to System>Administration>Hardware Drivers
and see if you have any to install. install them all and in a terminal type: ```
sudo apt-get update
```
check again for hardware drivers and then reboot.

---

### Post by Zionoxis on 2010-05-04
Thanks guys, this is a great help. I'll read the gparted section and hope it doesn't require an internet connection quite yet. (Still working on setting that one up.)

Ubuntu is beginning to look really amazing. I just hope I can get the time to learn how to use it. A completely editable OS sounds amazing to me...and to carry it around in portable form from any school computer to any other one sounds just as great. ;)

---

### Post by Simfan147 on 2010-05-04
Or go into Windows and search for Create and format a hard disk partition.

Your flash drive should show up. Right Click on it and choose either delete or reformat and that's it. Don't need to download anything or that crap.

---

### Post by techunit on 2010-05-04
Um you will have to delete the old partitions on the thumbdrive if he uses this windows method but I believe that it is possible.

It may not work because I am betting part of it was formated in EXT3

---

### Post by Simfan147 on 2010-05-04
Yes, I wasn't sure. It's been a while since I've had the need to fix my flash drive.

No, it'll work. I've done it before.

---

### Post by cgroza on 2010-05-04
Double post... Someone merge the two threads...  [http://ubuntuforums.org/showthread.php?p=9237877#post9237877](http://ubuntuforums.org/showthread.php?p=9237877#post9237877)

---

### Post by techunit on 2010-05-04
Good then either way works. I prefer gparted because it seems to work the best of all the partitioners.

---

