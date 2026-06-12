---
title: "file server and rsync"
date: 2012-05-09
forum: General Help
---

### Post by sirvoo on 2012-05-09
I have a Samba file server running on Ubuntu 11.10.

I plan on installing rsync to backup the server.

I have purchased a internal hard drive to store the back up files.

I have been reading people use external hdd to store the back ups.

Are there any benefit in using an external over internal hdd for the back up data?

---

### Post by sudodus on 2012-05-09
> **sirvoo said:**
> ...
Are there any benefit in using an external over internal hdd for the back up data?
Short answer: Yes, you can move it easily :-)

Long answer: A very good solution with an external HDD (eSATA or USB) is that you can have two backup drives, one attached to your computer and one somewhere else. If you want your family pictures to be safe in case of fire, theft etc, it is a good idea to have one backup copy far away from the computer, for example in another house.

---

### Post by sirvoo on 2012-05-09
2.5 or 3.5?

Does it matter what size I use? I would prefer a 2.5 as  I don't have to plug it into a power supply.

I'll see if I can exchange the internal hdd for an external one tomorrow.

---

### Post by sudodus on 2012-05-09
> **sirvoo said:**
> 2.5 or 3.5?

Does it matter what size I use? I would prefer a 2.5 as  I don't have to plug it into a power supply.

I'll see if I can exchange the internal hdd for an external one tomorrow.
I think you should consider
- convenience
- price/GB
- speed
- connection: eSATA (faster), USB 2 (most common), USB 3 (fastest)

You can find cases for standard (naked internal) HDDs to make them external drives. I suggest that you get a metal case, because it conducts the heat better and keeps the HDD cooler. But the most convenient alternative is to buy a ready-made external drive.

---

### Post by sirvoo on 2012-05-09
Actually I have a Vantec NexStar NST-D400S3 HDD Dock. It uses USB 3.

Do you think that will be fine?

The server only has USB 2 though, I wonder if I can install a USB 3 card, not sure if the motherboard will support USB 3.

The HDD is a WD Caviar Black 1TB.

I've been reading Green is better for backup and storage.

---

### Post by sudodus on 2012-05-09
> **sirvoo said:**
> Actually I have a Vantec NexStar NST-D400S3 HDD Dock. It uses USB 3.

Do you think that will be fine?

The server only has USB 2 though, I wonder if I can install a USB 3 card, not sure if the motherboard will support USB 3.

The HDD is a WD Caviar Black 1TB.

I've been reading Green is better for backup and storage.
I think you can start using the Vantec HDD Dock plugged into a USB 2 port. Rsync can be set to do incremental backup, and then it might be fast enough. Otherwise, I suggest that you install a USB 3 card. I don't think the mobo would complain or create problems, the card should manage the communication with external drive.

If you want to improve the life-time of the external drive, switch it off when it is not used (but of course, if you want automatic backup every night, it must be running every night).

---

### Post by sirvoo on 2012-05-09
The system will do a back up at 6pm at the end of the business day. I then turn the system off then turn it back on in the morning.

So there won't be any issues there.


Thanks for the help.

---

### Post by markbl on 2012-05-09
> **sirvoo said:**
> 
I plan on installing rsync to backup the server.

I back up my own machines in a similar way, but to an internal disk. You may want to consider using rsnapshot as I do. It is in the standard packages and is just a perl script which calls rsync but can create daily, weekly, monthly "snapshots". It uses symlinks so it produces a simple dated set of backup dirs but only uses space for the incremental file differences. I've been running it for many years and it works great.

---

### Post by sirvoo on 2012-05-13
I have 4 partition on the file server

/root  - ext4
/home  - ext4
/usr  - ext4
Virtual Memory

I have 2TB external HDD.

I only plan on creating 1 ext4 partition to store the backup with rsnapshot.

Do I need to create any more partition or is the 1 enough?

---

### Post by sirvoo on 2012-05-14
I've setup the USB Drive in the fstab file

UUID=xxx  /media/backup_disk_1 ext4 users,noauto 0 0

If I set it to auto mount on startup and the drive is not connect the system halts and waits for the drive to be connected so that is why I have set the automount off.

I've installed rsnapshot.

in the /etc/rsnapshot.conf

snapshot_root /media/backup_disk_1
no_create_root 1

rsnapshot configtest prints out
> ERROR: /etc/rsnapshot.conf on line 27:
ERROR: snapshot_root /media/backup_disk_1 - snapshot_root exists but is not \
         writable 
ERROR: /etc/rsnapshot.conf on line 230:
ERROR: backup /home/ localhost/ - snapshot_root needs to be defined before \
         backup points 
ERROR: /etc/rsnapshot.conf on line 231:
ERROR: backup /etc/ localhost/ - snapshot_root needs to be defined before \
         backup points 
ERROR: /etc/rsnapshot.conf on line 232:
ERROR: backup /usr/local/ localhost/ - snapshot_root needs to be defined \
         before backup points 
ERROR: ---------------------------------------------------------------------
ERROR: Errors were found in /etc/rsnapshot.conf,
ERROR: rsnapshot can not continue. If you think an entry looks right, make
ERROR: sure you don't have spaces where only tabs should be.

How do I set the disk to be writable?

---

### Post by hjclaes on 2012-05-14
Do you run your backup as root?

You may have to set the permissions on the mount point (or maybe also below).

# chmod 755 <directory>
# chown root.root <directory>

You also asked about performance and space needed for the disk. This depends on the tool you are using. With rsync you will need much more space than with storeBackup.

Storebackup does deduplication on a backup level for whole files and on a block level for image files also (if you want). In practice, this means, it recognizes if you mv / rename / copy files or directories and will not use additional space. Also, changes on the time stamp of a file are detected also. It also compresses files (you can define which ones.)
It uses hard links also, but the effort of a backup (starting from the second one) is incremental, the result is a full backup always.

Additionally, it has enhanced methods to delete old backups automatically.

Read [http://www.nongnu.org/storebackup/en/](http://www.nongnu.org/storebackup/en/) and / or [http://ubuntuforums.org/showthread.php?t=868244&highlight=storebackup](http://ubuntuforums.org/showthread.php?t=868244&highlight=storebackup) (or ask in this thread :popcorn: )

Regards

---

### Post by sirvoo on 2012-05-14
I am using rsnapshot

---

### Post by sirvoo on 2012-05-14
I have 
**sudo chown username\: /media/backup_disk_1**I now have access.

---

### Post by hjclaes on 2012-05-14
> **sirvoo said:**
> I am using rsnapshot

There are major differences to storebackup - but it depends on what you want and need.

> **sirvoo said:**
> I now have access. 	

:p

---

### Post by sirvoo on 2012-05-14
```
user@server:~$ rsnapshot hourly
Could not open logfile /var/log/rsnapshot.log for writing
Do you have write permission for this file?
```

What do I do now?

---

### Post by sirvoo on 2012-05-14
> user@server:~$ sudo rsnapshot hourly

works but does that mean the cron won't run now because it needs admin access?

---

### Post by hjclaes on 2012-05-14
I don't know the "correct" answer with sudo, but it should be possible to do:

$ sudo bash
# crontab -e

---

