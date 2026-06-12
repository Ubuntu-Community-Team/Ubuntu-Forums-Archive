---
title: "Scheduled backup of entire primary hard drive"
date: 2011-06-27
forum: General Help
---

### Post by kyutums on 2011-06-27
I have a headless Ubuntu server acting primarily as a file server. It has 2 hard drives - a primary 500GB drive and a recently added 1TB drive. The 1TB drive is partitioned to 2, each having 500GB.

The 500GB - the bootable disk - houses around 8 years of photos and movies. I want to back up the primary 500GB drive to one of the partitions on the 1TB disk. However, I would want a method that would allow me to easily restore the main 500GB should anything happen to it.

I was thinking of Clonezilla perhaps, and saving the image to one of the partitions on the 1TB. However, this would mean that I would have to restart the machine, boot via a USB disk, etc. Since this machine is on 24/7, I was hoping that there is a way to back up the main drive without any downtime.

Others suggested dd, but I'm not very good with cron and I'm a bit worried I might nuke the drive or the files if I fiddle with it. Also, I'm not sure if dd would work while the hard drive is mounted (it's running the main OS). :)

I'm using Ubuntu 10.10 and SimpleBackupSuite seems attractive. However, the wiki ([https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)) noted 48 open bugs so I was hoping there are other, more stable options. :)

---

### Post by electrojustin on 2011-06-27
Perhaps you could use RAID level 1 since you already have 2 drives-it writes mirrored data to both drives and (according to a quick Google search) seamlessly redirects requests to data once in the failed disk to a surviving mirror disk.

---

### Post by kyutums on 2011-06-27
Thanks electrojustin, but as per my understanding from the wiki ([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)), I can only implement this before I install Ubuntu. My machine already has it installed. :(

---

### Post by electrojustin on 2011-06-27
Sorry, I don't really know much about RAID-just heard of what it does.

---

### Post by Dave_L on 2011-06-27
I would use [rsync]("http://manpages.ubuntu.com/manpages/lucid/en/man1/rsync.1.html") or [rsnapshot]("http://manpages.ubuntu.com/manpages/lucid/en/man1/rsnapshot.1.html").

---

