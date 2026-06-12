---
title: "Help with sharing partition and map network drive"
date: 2009-07-14
forum: General Help
---

### Post by ultimatebuster on 2009-07-14
Hi!
I have a desktop PC set up with Ubuntu server 64 bit (9.04) with Gnome desktop installed. I also have SAMBA, webmin installed.

I partitioned the hard drive to:
/dev/sda1 (ext3) - boot, ubuntu
/dev/sda3 (ext4) - DATA

and a linux-swap partition.

The sda3 is mounted to /media/DATA at boot-up via fstab.

How do you share this partition/folder so that a Windows machine can **map it as a network drive?**

Thanks!

Edit NVM I got it

---

### Post by vezinadj on 2012-01-10
How did you end up accomplishing this? I am trying to do this right now actually and have a 500mb partition (data) and would like to configure it as a network drive. Any help would be great!

---

### Post by georgemc on 2012-01-10
a quick google search of this forum yielded the following:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

That should get you pointed in the right direction.

George

---

