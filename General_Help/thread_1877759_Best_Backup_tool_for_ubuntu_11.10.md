---
title: "Best Backup tool for ubuntu 11.10"
date: 2011-11-08
forum: General Help
---

### Post by alain.roger on 2011-11-08
Hi,

i'm new to ubuntu 11.10 and i would like know what is the best backup tool to save backuped data/image on an external USB disc or DVD-RW (if possible).
(for example, under Windows i know the Acronis true Image is a very good)

i would like to be able to recover very quickly my notebook installation in case of crash.

thank a lot.

A.

---

### Post by DapperMe17 on 2011-11-08
Rsync is a nice option, as a GUI.

---

### Post by linuxwin2 on 2011-11-09
CloneZilla live CD to backup/restore partition/disk

---

### Post by lolpenguin on 2011-11-09
If you like simplicity there's two options that are included by default:
If you don't mind the command line, you can use duplicity.
If you DO mind the command line, there is a front end for duplicity; deja-dup.
These take simplicity to new levels. When you start the deja-dup backup tool, it presents you with two options: Backup and Restore. Simple, yeah?

---

### Post by ballantony on 2011-11-09
> **lolpenguin said:**
> If you like simplicity there's two options that are included by default:
If you don't mind the command line, you can use duplicity.
If you DO mind the command line, there is a front end for duplicity; deja-dup.
These take simplicity to new levels. When you start the deja-dup backup tool, it presents you with two options: Backup and Restore. Simple, yeah?

like lolpenguin says.  Use deja-dup to get yourself backed up quickly and easily (it even saves up to 5Gb on Ubuntu One by default)  Then use grsync for finer control

---

### Post by alain.roger on 2011-11-09
> **DapperMe17 said:**
> Rsync is a nice option, as a GUI.

Thank for help. I've checked it and i have a little issue with it.
basically my backup should be stored on another HDD which is also in the same notebook.
unfortunatelly this 2nd HDD is mounted in order to receive the backuped files.... but as it is mounted in /mnt/2ndhd, the backup process saves it also, so it is not ending storing as it saves what it saved before and so on ...

is there a way to exclude a path or a part of directory ?

thx

---

### Post by oldfred on 2011-11-09
I know in rsync you can exclude things. If in a script you could unmount it and then remount it also.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
[http://flyback-project.org/](http://flyback-project.org/)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

With rsync
# -l: copies symlinks as symlinks
# r - recursive / subdirectories

From my backup script where I choose specific partitions to copy. I exclude thumbnails.

rsync -aurvlP --exclude '.thumbnails' /home /mnt/Backup

---

### Post by GSD4ME on 2011-11-11
Am interested in these views but in my opinion Deja Dup is *not* the tool it could or should be.

- It is too simple minded - eg I want to do separate backups for certain folders - bigger ones to an external HDD, others to Ubuntu One. Very difficult (if not impossible?) to set up DD to do this.
- It backs up *everything* in a folder - specifically the 'hidden' files and folders. Bug reports on the various technical sites have highlighted this as a feature that could be vastly improved upon.
- DD has problems working with ubuntu 11.10 and Ubuntu One - synchronization problems and bugs mean that I for one cannot do the backups that were working perfectly in previous versions of Ubuntu, so I await updates but I am not holding my breath for a quick resolution

So at the moment, I am 'living on a prayer', with no backups being done at all so I would be most interested in a good, established and easy to use backup tool.

---

### Post by haqking on 2011-11-11
For me (as backup strategies are a personal preference)

Clonezilla for a fresh install
Clonezilla after updates and customisation

The a daily cron job using rsync for personal files/docs etc.

A restore for me takes about 5 to 30 minutes depending at what level i restore.

For my desktop system that is.

---

