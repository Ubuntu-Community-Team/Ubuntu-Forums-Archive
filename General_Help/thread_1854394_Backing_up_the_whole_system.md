---
title: "Backing up the whole system"
date: 2011-10-04
forum: General Help
---

### Post by nir2000 on 2011-10-04
Hi everybody!
I want to backup all my system to a removable hard-drive.
That includes the operating system and all files.
The result that i am expecting in a case of disk failure is that I will be able to connect my backup drive through a USB, install my new drive and copy somehow the backed up drive to the newly installed drive.
I have heard of cloneZilla and the command dd to somehow achieve those goals but i am not sure if that will achieve my targets.
The second problem is that I don't understand where should I put the backup software , and do I need an operating system on the removable hard disk.
Thank you in advance.
Nir

---

### Post by Frogs Hair on 2011-10-04
These are two options I know of .

[http://clonezilla.org/](http://clonezilla.org/)  

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by Manyette on 2011-10-04
I use and recommend clonezilla to you.  I use it regularly and it will do a bare metal backup.  You do not need an OS on the external drive.  Only need to format is in something like ext3 or ext4, and be sure to uncheck the "take ownership" of the drive. Clonezilla can put your entire system back on a brand new drive.

---

### Post by collisionystm on 2011-10-04
> **nir2000 said:**
> Hi everybody!
I want to backup all my system to a removable hard-drive.
That includes the operating system and all files.
The result that i am expecting in a case of disk failure is that I will be able to connect my backup drive through a USB, install my new drive and copy somehow the backed up drive to the newly installed drive.
I have heard of cloneZilla and the command dd to somehow achieve those goals but i am not sure if that will achieve my targets.
The second problem is that I don't understand where should I put the backup software , and do I need an operating system on the removable hard disk.
Thank you in advance.
Nir

Use Clonezilla to do a full backup of your system.

Once you have made a clonezilla image, just use rsync in crontab to do nightly backups of your /home folder to get your udpated files as the days go by. That way, you restore your OS from clonezilla and then your updated files from the rsync backup.

---

### Post by seawolf167 on 2011-10-04
I'll add another +1 for [Clonezilla]("http://www.clonezilla.org"). I make images every couple months or so then use [rsync ]("https://help.ubuntu.com/community/rsync")(or [sbackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite"), more [options here]("https://help.ubuntu.com/community/BackupYourSystem")) to create daily backups of all my important data.

---

### Post by Ralph L on 2011-10-04
LuckyBackup is a gui front end for rsync if that is of interest to you.

---

### Post by seawolf167 on 2011-10-04
> **Ralph L said:**
> LuckyBackup is a gui front end for rsync if that is of interest to you.

[Grsync]("https://help.ubuntu.com/community/rsync#Grsync") is another front-end for rsync

```
sudo apt-get install grsync
```

---

