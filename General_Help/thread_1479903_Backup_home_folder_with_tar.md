---
title: "Backup home folder with tar"
date: 2010-05-11
forum: General Help
---

### Post by Kvik on 2010-05-11
Hi

I want to take a backup of my home folder to a USB drive, and i've been told the easy way is to use the terminal and pack it with tar, but i can't figure it out, and i don't want to backup mucis and video. Any one that can help me?

---

### Post by Grenage on 2010-05-11
So you want everything but certain file types backed up, or everything but certain folders?

---

### Post by Kvik on 2010-05-12
I want to backup my home folder - video and music i want it in a tar fil, and backup to a USB without haveing the backup on local HD

---

### Post by notbitmonk on 2010-05-12
Connect the USB drive.  Select the files and folders that you want to copy, right click and select Send to.  On the next window select the USB drive, enter a name and select the compression type (.zip, tar.gz or tar.bz2).  If the files you do not want to copy are just everywhere.  Move them all to a folder and do not select that folder on the copy process.

---

### Post by sarin_cv on 2010-05-12
this is a part of script i am using

# Backup
  suffix=`date '+%Y%m%d_%H%M'`
  sudo tar -cpzf "backup_$suffix.tgz" --exclude=/home/sarin/music /home/sarin/


this will take a backup of /home/sarin/Documents excluding /home/sarin/music


the easy way is to use the application named 'back in time' ... here we can specify which folders to backup and what type of files are to be excluded etc..

---

### Post by Kvik on 2010-05-12
Hi

back in time looks okay, but it don't compress it (zip, tar)

---

### Post by nilsma on 2010-05-24
> **notbitmonk said:**
> Connect the USB drive.  Select the files and folders that you want to copy, right click and select Send to.  On the next window select the USB drive, enter a name and select the compression type (.zip, tar.gz or tar.bz2).  If the files you do not want to copy are just everywhere.  Move them all to a folder and do not select that folder on the copy process.

I have to buy a new HD shortly and i am going to re-install 10.04 Lucid, how would i go about "reinstalling" my backed-up home folder using the above mentioned backup-method after reinstalling 10.04 Lucid? 

The compressed backup of my home folder is on an external HD - will the "reinstallation of my home folder" also set my firefox and evolution back to the original state?

---

### Post by jerome1232 on 2010-05-24
If the bulk of your data is music/pictures/video the compression is mostly a huge waste of cpu processing power anyways, since multimedia is already highly compressed, re-compressing just wastes time and won't save you much space.

I would just create a big fat tar (uncompressed) of my home folder and put it on the external drive. To restore you just extract the tar back over your new home and everything should be peachy.

---

