---
title: "How to format a write protected flash drive"
date: 2010-10-12
forum: General Help
---

### Post by SpicyBaconator on 2010-10-12
So I have a flash drive that is write protected and in RAW format(so not formatted). I've tried everything I can find to make it usable again in Windows but I ran out of options. I quickly found about the Gnome Partition Editor, but when I try to start it, it gets an icon in the taskbar that says "Starting GParted" and then it closes. Is some other way I can format my flash drive or do I need to find out why gparted isn't running?

---

### Post by Peter09 on 2010-10-12
Some flashdrives actually have a little switch on the side which write protects the drive, might be worth check to see if thats your problem.

---

### Post by SpicyBaconator on 2010-10-12
Yeah that was the first thing I checked. When I said I ran out of options I wasn't joking. I spent a good three hours researching this for Windows.

---

### Post by Peter09 on 2010-10-12
Try running gparted from a terminal, it may provide some debug information.

---

### Post by SpicyBaconator on 2010-10-12
Ok I did get some debug info, but of course I have no idea what it means. Here is the terminal screen:
matt@ubuntu:~$ sudo gparted
[sudo] password for matt: 
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
matt@ubuntu:~$

Edit: I see that this is known bug, but I can't find any solutions.

---

### Post by rick550 on 2010-10-12
burn this to disk and it will work 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

change it to your flash drive or you will risk messing up a hard drive partition

---

### Post by SpicyBaconator on 2010-10-12
That did allow me to run gparted, so thanks! But unfortunately, gparted was unable to delete the existing partition or format it because the drive is read only. Is there a way to change read-write permissions for a flash drive?

Edit: I tried "sudo chmod 777 /dev/sdb" and "sudo chmod 777 /dev/sdb1" and neither gave me any kind of feedback, but it did not work because the drive is still read only. /dev/sdb and /dev/sdb1 are the only possible names I can find for it. I'm pretty sure it doesn't have an actual location I can navigate to because it's not formatted.

---

