---
title: "How to backup the whole kit and caboodle"
date: 2011-06-05
forum: General Help
---

### Post by johnmarkzimm on 2011-06-05
I just started using Linux four days ago and I feel like I just came out of the OS closet! I love my Ubuntu 11.04 (classic look). I have been playing around with it so much. I also have a new setup of Windows 7 on a partition. But I haven't even looked around on that side... no need. This may be my old ways of thinking, but I am getting worried that I will loose all this setup work/time by some simple error. I would love to backup a perfect copy of the whole thing. I saw a program called Mondo Rescue, but it will not work with 11.04. Does anyone have any other suggestions... Thanks!

---

### Post by wildmanne39 on 2011-06-05
> **johnmarkzimm said:**
> I just started using Linux four days ago and I feel like I just came out of the OS closet! I love my Ubuntu 11.04 (classic look). I have been playing around with it so much. I also have a new setup of Windows 7 on a partition. But I haven't even looked around on that side... no need. This may be my old ways of thinking, but I am getting worried that I will loose all this setup work/time by some simple error. I would love to backup a perfect copy of the whole thing. I saw a program called Mondo Rescue, but it will not work with 11.04. Does anyone have any other suggestions... Thanks!Hi, go into software center or synaptic and put sbackup in the search box and it will bring it up then you can install it, it uses a easy interface for backing up and restoring file or drives. In my menu it is called simple backup configuration.

---

### Post by ladlers on 2011-06-05
Here's a quickie I found in one of the forums. I haven't tested it in that I backed up a partition but never restored one (no acid test):
To backup partition sda2 to a file named backup.dat in the backup folder on /media/sdc1:

sudo dd if=/dev/sda2 | sudo gzip > /media/sdc1/backup/backup.dat

the folder backup must exist on /media/sdc1. To restore, boot the ubuntu trial cd, press cntl-alt-f1, mount the devices and issue:

gzip -dc /media/sdc1/backup/backup.dat | sudo dd of=/dev/sdb1


This method also compresses the backup file to save space. I used this on Slackware so perhaps you need to add or remove sudos. Lots of luck.

---

### Post by dFlyer on 2011-06-05
Clonezilla will do the trick.

---

### Post by ladlers on 2011-06-30
Unfortunately, tried but not true. The DD/GZIP method doesn't work as I just tried restoring my Slackware linux due to upgrading it when the connection broke. Luckily, I had another backup created by Paragon Disk Backup, a program I found to be free once a year which backs up both windows partitions and linux partitions. I still had to run chroot /media/sda2 lilo and modify the /etc/fstab, but it is quite fully recovered. Sorry for the false information. I read it on another linux forum.

---

### Post by seawolf167 on 2011-06-30
> **dFlyer said:**
> Clonezilla will do the trick.

Big +1 for Clonezilla

---

### Post by Mark Phelps on 2011-06-30
Another +1 for Clonezilla.  

Not only will it allow you to image off the entire drive (i.e., ALL the partitions on the drive), it will also allow you to image off (and restore) individual partitions.

---

### Post by polki@mac.com on 2011-07-01
+1 for clonezilla. I use it at work to back-up one machine and restore lots of machines with that machine. I do it via ssh. Works perfectly!

---

### Post by indytim on 2011-07-01
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

fsarchiver is bundled within the SysRescue LiveCD


IndyTim / DataMan

---

