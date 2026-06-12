---
title: "Backup documents"
date: 2012-09-13
forum: General Help
---

### Post by zhanfei on 2012-09-13
I am new here, so I am not sure if it is proper to ask my question here. Sorry if it isn't.
 
I want to have backups for all the useful files on my laptop with ubuntu OS. So I bought a portable hard disk. Then my question is: Does anybody know a command which only replaces the renewed files on the laptop to the external disk?

---

### Post by kimberlite on 2012-09-13
Try out one of the backup tools with graphical UI. Personally I use Deja Dup. There are a [review]("http://apcmag.com/the-best-ubuntu-backup-tools.htm") and a [wiki help page]("https://help.ubuntu.com/community/BackupYourSystem") you may want to consult.

---

### Post by mastablasta on 2012-09-13
+1 for deja dup.
 
another nice GUI option is Mintbackup tool
[IMG]http://community.linuxmint.com/img/screenshots/mintbackup.png[/IMG]
[http://community.linuxmint.com/software/view/mintbackup](http://community.linuxmint.com/software/view/mintbackup)
 
dd command can be used to clone data, however it is dangerous if used wrong.
 
rsync (or GUI grsync) is used for incremental backups and syncing (i.e. when you set a folder to be backed up every day at 12:00 for example).
 
if you want to clone the drive you can use clonezilla or Redo Backup

---

### Post by jerrrys on 2012-09-13
You already have rsync installed by default, so ill give it a plug :)

Grsync and LuckyBackup are both GUI's for rsync and work quite nice for me.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=grsync&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=grsync&as_qdr=all&sa=Google+Search&lang=en)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=luckybackup&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=luckybackup&as_qdr=all&sa=Google+Search&lang=en)

Both are in the software center.

And as mention, Clonezilla is good for cloning HDD's or partitions.

---

### Post by kjohri on 2012-09-14
> Then my question is: Does anybody know a command which only replaces the renewed files on the laptop to the external disk?

rsync is the command by which you can only backup the files which have changed since the last time (rsync) command was run. This link gives the details,

[http://www.softprayog.in/tutorials/rsync-tutorial]("http://www.softprayog.in/tutorials/rsync-tutorial")

---

### Post by vasa1 on 2012-09-14
> **zhanfei said:**
> I am new here, so I am not sure if it is proper to ask my question here. Sorry if it isn't.
 
I want to have backups for all the useful files on my laptop with ubuntu OS. So I bought a portable hard disk. Then my question is: Does anybody know a command which only replaces the renewed files on the laptop to the external disk?

Stay with the one that comes with your distro and try to understand it thoroughly.

---

### Post by Bucky Ball on 2012-09-14
Unison is good too. It syncs two directories, across the network if you like, and has GUI. In the repos.

---

