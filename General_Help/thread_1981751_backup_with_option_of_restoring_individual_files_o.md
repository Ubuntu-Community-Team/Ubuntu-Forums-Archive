---
title: "backup with option of restoring individual files only"
date: 2012-05-17
forum: General Help
---

### Post by bertmung on 2012-05-17
I'm using Backup to automatically make backups of my data.

I need to restore a single corrupted file. It looks like backup only allows all the data to be restored. Fortunately I can restore to a separate folder instead of rewriting everything.

I find that the problem of needing a backup of a single file comes up much more often that having all my data wiped out. What is the best way to make backups in a way that allows restoration of single files? 

BTW I'm going to keep doing mass backups of my data. Losing everything may be rare, but potentially catastrophic.

---

### Post by dyfi on 2012-05-17
Have a look at "Backintime"

---

### Post by forrestcupp on 2012-05-17
I use LuckyBackup, which is a graphical frontend for rsync. Instead of compressing the backup into an unreadable file, it makes a 1:1 backup where you can actually look on your external HD and see the files. That way, you can copy over anything you want. Another good thing about LuckyBackup is that it only backs up the files that have changed.

---

### Post by ajgreeny on 2012-05-17
Although many would say it is not really meant as a backup tool, though I'm not sure why they say that, I have been using rsync successfully for several years now, and find it does everything I want.

I use command ```
rsync -r -n -t -p -v  /home/<user>/ /media/Iomega/1004/
``` and it takes only a few minutes, or occasionally seconds, if there are only a few new or changed files, to backup everything from my home to the Iomega external disk.

I can then restore everything if needed, or just pick a single file from the 1004 folder on the external disk and restore that alone.

Simple but effective, in my opinion.

---

### Post by bertmung on 2012-05-17
rsync might solve another problem

I have data that I want to use at the desktop and on a remote laptop. It is too sensitive to upload to the cloud. Could I use rsync to update files to a thumb drive and then update them to the desktop if I make changes to the files on the thumb drive?

---

### Post by ajgreeny on 2012-05-17
> **bertmung said:**
> rsync might solve another problem

I have data that I want to use at the desktop and on a remote laptop. It is too sensitive to upload to the cloud. Could I use rsync to update files to a thumb drive and then update them to the desktop if I make changes to the files on the thumb drive?
You could, but for that something like **unison** might be better. It's in the repos.

---

### Post by Habitual on 2012-05-17
Up until now I was using a manual unison.sh script.
My WDC 3.1T USB3 Drive turned into a brick and I have no secondary backup.

I could always mount my own cloud which IS secure, or s3fs (fuse-over-amazon) to an S3 BitBucket or to any server of my choice at our DC.
I could rsync to anywhere since I have a key already in place.

Personally, I prefer unison for sync'ing to /media/removable

---

### Post by Ms. Daisy on 2012-05-18
> **bertmung said:**
> rsync might solve another problem

I have data that I want to use at the desktop and on a remote laptop. It is too sensitive to upload to the cloud. Could I use rsync to update files to a thumb drive and then update them to the desktop if I make changes to the files on the thumb drive?
You can rsync directly from the remote laptop to the desktop using ssh.

---

