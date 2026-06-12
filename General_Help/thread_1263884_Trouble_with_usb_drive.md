---
title: "Trouble with usb drive"
date: 2009-09-11
forum: General Help
---

### Post by roscowgo on 2009-09-11
I have a usb drive that is stuck on root:root ownership.   It Seemed to happen today after I installed the xubuntu desktop enviroment, but it could have been earlier.

I can read files (view, play, copy to Desktop etc) fine from the drive, but not write, when I try to unmount it tells me the drive is busy.  Chown returns nothing but doesn't manage to change any permissions.

for instance a test folder with the old tabula rasa installer in it.

willg@willgx:/media/New Volume$ ls -l test
total 2878784
-rwxrwxrwx 1 root root 2947869048 2008-02-02 22:06 install_tabula_rasa_1.4.6.0.exe
drwxrwxrwx 1 root root          0 2008-02-07 14:26 Tabula Rasa Installer
willg@willgx:/media/New Volume$ chown -R willg:willg test
willg@willgx:/media/New Volume$ ls -l test
total 2878784
-rwxrwxrwx 1 root root 2947869048 2008-02-02 22:06 install_tabula_rasa_1.4.6.0.exe
drwxrwxrwx 1 root root          0 2008-02-07 14:26 Tabula Rasa Installer
willg@willgx:/media/New Volume$ 

I've tried restarts. power on/offs of the drive... nada.    Any suggestions?

Oh, almost forgot, after I installed the xubuntu desktop I did install some updates.   xubuntu-desk is now removed but not purged and I'm running in gnome.:confused:

---

### Post by Liolikas on 2009-09-11
sudo chown -R your_name /media/new_vol/*

---

### Post by roscowgo on 2009-09-11
I was in the midst of creating a new mount point and trying a chown with sudo su when I read your message.     Results of trying to chown the contents:

root@willgx:/media/New# sudo chown -R willg /media/New/*
chown: cannot access `/media/New/backuo/home/willg/.Trash/netloony/NetLoony/src/org/netloony/inout': Input/output error

and it just started going down the list with i/o errors after that.  

Still mounts and reads everything fine.

---

### Post by roscowgo on 2009-09-11
It appears to be a failing physical disk.


O well.

---

