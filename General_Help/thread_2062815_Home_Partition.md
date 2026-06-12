---
title: "Home Partition"
date: 2012-09-25
forum: General Help
---

### Post by dieselglock on 2012-09-25
Hello,

I repartitioned my drive to add a home only partition to allow an easier upgrade from 10.04lts to 12.4 lts. I followed this tutorial in this link. [http://ubuntuforums.org/showthread.php?p=9141619](http://ubuntuforums.org/showthread.php?p=9141619) I made it to the step 3. F. all seemed well. The problem I have is that I get this error on reboot: Could not update ICEauthority file/home/lawrence/.ICEauthorty.

I have searched the forums for this error and found some posts but am confused. I am not a Ubuntu pro. Any help would be very appreciated.

Lawrence

---

### Post by oldfred on 2012-09-25
#Replace all instances of username with your login name or use $USER
#This should be your username:
echo $USER

.dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
chmod 755 /home/username
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.


Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/$USER/.dmrc
sudo chown $USER:$USER /home/username

---

### Post by dieselglock on 2012-09-25
Thanks for replying. I have tried to go to first link you mentioned. I tried the first 2 commands and get errors cannot access /home/lawrence No such file or directory and cannot access .dmrc No such file or directory.
I am probably doing something wrong here. I am not good at this stuff. Please help.

---

### Post by oldfred on 2012-09-25
Post this command, it should be like mine:

fred@fred-Precise:~$ ls -la $HOME/.ICEauthority
-rw------- 1 fred fred 36598 Sep 21 23:36 /home/fred/.ICEauthority

---

### Post by dieselglock on 2012-09-26
Hello again,
I have got the laptop to boot again as normal by reversing the fstab entry for the new partition. I have the new partition prepared and have tried 3 different guides on how to move my home to the new partition and then getting to to work when rebooting and not having any luck.
Here is the output you requested.
lawrence@lawrence-laptop:~$ ls -la $HOME/.ICEauthority
-rw-rw-rw- 1 lawrence lawrence 74694 2012-09-25 21:47 /home/lawrence/.ICEauthority

Thanks

---

### Post by oldfred on 2012-09-26
Your permissions are -rw-rw-rw- or 666 and mine are -rw------- or 600. So it looks like the permissions still need to be changed. My notes said 644 was correct, so now I do not know what really works. 

Almost all files in home are 664 and directories are 775. But a few need special settings and some you may change to add execution or other changes yourself.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

More discussion on permissions on a data partition.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)

Other instructions that have worked:
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
Note: cp without -a means root takes ownership which would be a big issue

---

### Post by dieselglock on 2012-09-26
Hello Fred,  
Thanks for your help. I have tried just about everything and deleted and repartitioned 3 times and followed all the instructions.  I still cant get this to work. I am thinking of just doing a fresh install with a separate home partition and starting from scratch. 

Lawrence

---

### Post by oldfred on 2012-09-26
I actually do not have a separate partition for /home anymore. I do have two data partitions for most of the data that is in /home but none of the usually hidden settings. My /home is about 2GB and most of that is .wine, so now it is part of my / (root). 

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

